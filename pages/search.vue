<template>
  <div class="main-container">
    <Header/>
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
    <Footer/>
  </div>
</template>

<script>
import Header from '~/components/Header/Header.vue'
import Grid from '~/components/Grid/Grid.vue'
import GridItem from '~/components/Grid/GridItem.vue'
import ProductBox from '~/components/ProductBox/ProductBox.vue'
import Footer from '~/components/Footer/Footer.vue'
import productData from '~/mockData/Search.json'

export default {
  components: {
    Header,
    Grid,
    GridItem,
    ProductBox,
    Footer
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
