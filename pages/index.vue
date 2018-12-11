<template>
  <section class="section">
    <div class="container">
      Home Page
      <NuxtLink :to="'/search'">
        Go to Search
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
</style>
