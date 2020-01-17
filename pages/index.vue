<template>
  <section class="section">
    <div class="container">
      <img
        src="https://www.williams-sonoma.com/wsimgs/ab/images/dp/ecm/201928/3345/001/007.jpg"
        alt="Destination: France">
      <img
        src="https://www.williams-sonoma.com/wsimgs/ab/images/dp/ecm/201928/1840/001/027.jpg"
        alt="Schumacher by Williams Sonoma">
      <NuxtLink :to="'/shop'">
        Go to Shop
      </NuxtLink>
    </div>
  </section>
</template>

<script>
import Header from '~/components/Header/Header.vue'
import Footer from '~/components/Footer/Footer.vue'
import NuxtLink from '~/.nuxt/components/nuxt-link.js'

export default {
  components: {
    Header,
    NuxtLink,
    Footer
  }
}
</script>

<style>
img {
  width: 100%;
}
</style>
