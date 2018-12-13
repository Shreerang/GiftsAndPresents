<template>
  <section class="section">
    <div class="container">
      <div class="prod-must-show">
        <img
          src="https://via.placeholder.com/400"
          alt="Product">
        <button
          type="button"
          class="btn-atb">
          Add to bag
        </button>
      </div>
      <div class="prod-details">
        <div class="prod-details-title">
          <strong>Brown eggs</strong>
        </div>
        <div class="prod-details-rating">
          <StarRating
            :rating="4.2"
            :total-reviews="113"/>
        </div>
        <div class="prod-details-desc">
          <strong>Product details</strong>
          <p>All product description. Raw organic brown eggs in a basket</p>
        </div>
        <div class="prod-details-qs">
          <QuantitySelector :icon-dimensions="16"/>
        </div>
        <div class="prod-details-vs">
          <VarianceSelector
            :variance-data="sizeSelectorData"
            label-name="Size"
            label-default-value="Please select a size"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import StarRating from '~/components/StarRating/StarRating'
import QuantitySelector from '~/components/QuantitySelector/QuantitySelector'
import VarianceSelector from '~/components/VarianceSelector/VarianceSelector'
export default {
  components: {
    StarRating,
    QuantitySelector,
    VarianceSelector
  },
  data() {
    return {
      sizeSelectorData: [
        { name: 'Xtra Small', value: 'XS' },
        { name: 'Small', value: 'S', availability: false },
        { name: 'Medium', value: 'M', availability: false },
        { name: 'Large', value: 'L' },
        { name: 'Xtra Large', value: 'XL' },
        { name: 'Double XL', value: 'XLL' }
      ]
    }
  }
}
</script>

<style>
.container {
  display: flex;
  flex-flow: row;
}
.prod-must-show {
  position: sticky;
  top: 64px;
  bottom: 0;
  width: 30%;
  /* padding: 1rem; */
  display: table;
  text-align: center;
}
.btn-atb {
  padding: 1rem;
  width: 100%;
  background: #c00;
  color: #fff;
  font-size: 1em;
  max-width: 400px;
  margin-top: 10px;
  box-sizing: border-box;
}
.prod-details {
  width: 70%;
  padding: 1rem;
}
.prod-details-title {
  padding: 0 0 10px 0;
  font-size: 1.5em;
}
.prod-details-rating {
  padding: 10px 0;
}
.prod-details-desc {
  padding: 10px 0;
  font-size: 1em;
}
.prod-details-desc strong {
  font-size: 1.1em;
  padding: 0 0 10px 0;
  width: 100%;
  display: block;
}
.prod-details-desc p {
  font-size: 1em;
  padding: 10px 0;
}
.prod-details-qs {
  padding: 10px 0;
}
.prod-details-vs {
  padding: 10px 0;
}
.nugget-variance-shape:nth-child(1) {
  margin-left: 0;
}

/* Small devices (landscape phones, less than 768px) */
@media all and (max-width: 767.98px) {
  .container {
    display: block;
  }
  .prod-must-show {
    width: 100%;
    position: relative;
    top: 0;
    display: table;
    vertical-align: middle;
    text-align: center;
  }
  .prod-details {
    width: 100%;
  }
}

/* Extra small devices (portrait phones, less than 576px) */
@media all and (max-width: 575.98px) {
  .prod-must-show img {
    width: 99%;
  }
}
</style>
