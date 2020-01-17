<template>
  <div
    v-if="rating > 0"
    class="nugget-stars">
    <div>
      <component
        v-for="n of totalStars"
        :key="n"
        :is="currentComponent(n)"
        :fill-color="colorType(n)"
        :base-color="baseColor"
        :rating="rating"
        :icon-dimensions="iconDimensions"
      />
    </div>
    <div
      v-if="totalReviews"
      class="nugget-reviews">
      {{ "(" + totalReviews + ") reviews" }}
    </div>
  </div>
  <div
    v-else
    id="nugget-stars-no-rating">
    {{ noRatingMsg }}
  </div>
</template>

<script>
// Can Star and PartialStar components be dynamically imported?
import Star from './Star'
import PartialStar from './PartialStar'

// Using a global variable like this - Good or bad?
let isPartialRendered = false
export default {
  name: 'StarRating',
  components: {
    Star,
    PartialStar
  },
  props: {
    totalStars: {
      type: Number,
      default: 5
    },
    iconDimensions: {
      type: Number,
      default: 20
    },
    rating: {
      type: Number,
      default: 0
    },
    fillColor: {
      type: String,
      default: '#000'
    },
    baseColor: {
      type: String,
      default: '#CCC'
    },
    noRatingMsg: {
      type: String,
      default: 'Be the first to review!'
    },
    totalReviews: {
      type: [Number, String],
      default: 0
    }
  },
  methods: {
    currentComponent: function(count) {
      const int_part = Math.trunc(this.rating)
      if (count > int_part && isPartialRendered === false) {
        isPartialRendered = true
        // Re-setting the isPartialRendered flag here, for cases where the Partial SVG is the last SVG
        if (count === this.totalStars) {
          isPartialRendered = false
        }
        return 'PartialStar'
      } else {
        if (count === this.totalStars) {
          isPartialRendered = false
        }
        return 'Star'
      }
    },
    colorType: function(n) {
      return this.rating - n > -1 ? this.fillColor : this.baseColor
    }
  }
}
</script>

<style scoped>
.nugget-stars {
  display: table;
}
.nugget-stars > div {
  display: table-cell;
  vertical-align: middle;
}
.nugget-reviews {
  padding-left: 7px;
}
</style>
