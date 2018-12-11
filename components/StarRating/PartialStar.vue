<template>
  <svg
    :width="iconDimensions"
    :height="iconDimensions"
    x="0px"
    y="0px"
    viewBox="0 0 306 306"
    xml:space="preserve"
  >
    <defs>
      <linearGradient :id="randomId">
        <stop
          :stop-color="fillColor"
          offset="0%" />
        <stop
          :offset="offsetValue"
          :stop-color="fillColor" />
        <stop
          :offset="offsetValue"
          :stop-color="baseColor" />
        <stop
          :stop-color="baseColor"
          offset="100%" />
      </linearGradient>
    </defs>
    <g :fill="'url(#' + randomId + ')'">
      <polygon
        points="153,230.775 247.35,299.625 211.65,187.425 306,121.125 191.25,121.125 153,6.375 114.75,121.125 0,121.125 94.35,187.425 58.65,299.625"
      />
    </g>
  </svg>
</template>

<script>
export default {
  name: 'PartialStar',
  props: {
    rating: {
      type: Number,
      required: true
    },
    iconDimensions: {
      type: Number,
      default: 20
    },
    baseColor: {
      type: String,
      default: '#CCC'
    },
    fillColor: {
      type: String,
      default: '#C00'
    }
  },
  data() {
    return {
      // Is this the right way to do things?
      randomId: 'partialFill_' + Date.now()
    }
  },
  computed: {
    offsetValue: function() {
      const int_part = Math.trunc(this.rating)
      let float_part = Number((this.rating - int_part).toFixed(2))
      return float_part * 100 + '%'
    }
  }
}
</script>

<style scoped>
</style>
