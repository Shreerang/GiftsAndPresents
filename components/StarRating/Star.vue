<template>
  <svg
    :width="iconDimensions"
    :height="iconDimensions"
    x="0px"
    y="0px"
    viewBox="0 0 306 306"
    xml:space="preserve"
  >
    <g>
      <polygon
        :fill="fillColor ? fillColor : baseColor"
        points="153,230.775 247.35,299.625 211.65,187.425 306,121.125 191.25,121.125 153,6.375 114.75,121.125 0,121.125 94.35,187.425 58.65,299.625"
      />
    </g>
  </svg>
</template>

<script>
export default {
  name: 'Star',
  props: {
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
  }
}
</script>

<style scoped>
</style>
