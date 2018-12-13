<template>
  <div class="main-container">
    <section class="section">
      <div class="container">
        <Grid>
          <GridItem
            v-for="(item, index) in gridData"
            :key="index">
            <ProductBox :product="item"/>
          </GridItem>
        </Grid>
      </div>
    </section>
  </div>
</template>

<script>
import Grid from '~/components/Grid/Grid.vue'
import GridItem from '~/components/Grid/GridItem.vue'
import ProductBox from '~/components/ProductBox/ProductBox.vue'
import productData from '~/mockData/Search.json'

export default {
  components: {
    Grid,
    GridItem,
    ProductBox
  },
  data() {
    return {
      gridData: productData
    }
  }
}
</script>

<style>
.card {
  box-shadow: none;
}
.card-content {
  padding: 1rem;
}
</style>
