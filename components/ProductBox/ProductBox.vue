<template>
  <NuxtLink
    :to="'/product/'+product.id"
    class="link">
    <img
      :src="product.image"
      alt="Placeholder image"
      class="prod-img">
    <p class="prod-title">{{ product.title }}</p>
    <p class="prod-price">${{ product.price }}</p>
    <StarRating
      :rating="product.rating"
      class="prod-stars"/>
    <p class="prod-desc">{{ product.desc }}</p>
  </NuxtLink>
</template>

<script>
import StarRating from '~/components/StarRating/StarRating.vue'
import NuxtLink from '~/.nuxt/components/nuxt-link.js'
export default {
  name: 'ProductBox',
  components: {
    StarRating,
    NuxtLink
  },
  props: {
    product: {
      type: Object,
      default: () => ({
        title: 'Title',
        desc: 'Description',
        rating: 3
      })
    }
  }
}
</script>

<style>
.prod-img {
  width: 100%;
}
.prod-title {
  font-size: 14px;
  padding: 5px 0;
  font-weight: bold;
}
.prod-price {
  font-weight: bold;
  padding: 5px 0;
  color: #000;
}
.prod-stars {
  width: 100%;
  padding: 5px 0;
}
.prod-desc {
  padding: 5px 0;
}
.link {
  text-decoration: none;
  color: #000;
}
</style>
