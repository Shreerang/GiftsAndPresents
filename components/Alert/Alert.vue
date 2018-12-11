<template>
  <div
    v-if="alertType === 'error' && isActiveData"
    :style="alertStyle"
    class="nugget-error">
    <slot />
  </div>
  <div
    v-else-if="alertType === 'warning' && isActiveData"
    :style="alertStyle"
    class="nugget-warning"
  >
    <slot />
  </div>
</template>

<script>
export default {
  name: 'Alert',
  props: {
    alertType: {
      type: String,
      default: 'error'
    },
    alertPosition: {
      type: String,
      default: 'global'
    },
    isActive: {
      type: Boolean,
      default: false
    },
    persistFor: {
      type: Number,
      default: 5
    }
  },
  data() {
    return {
      isActiveDataVal: this.isActive
    }
  },
  computed: {
    isActiveData: {
      get: function() {
        return this.isActiveDataVal
      },
      set: function(val) {
        this.isActiveDataVal = val
      }
    },
    alertStyle() {
      if (this.alertPosition === 'global' && this.alertType === 'error') {
        return {
          border: 'solid 1px red',
          padding: '10px'
        }
      }
      if (this.alertPosition === 'global' && this.alertType === 'warning') {
        return {
          border: 'solid 1px orange',
          padding: '10px'
        }
      }
    }
  },
  watch: {
    isActive: function() {
      this.isActiveDataVal = this.isActive
    },
    isActiveData: function() {
      if (this.isActiveData) {
        const getElm =
          this.alertType === 'error' ? 'nugget-error' : 'nugget-warning'
        var checkElm = setInterval(
          function() {
            if (document.getElementsByClassName(getElm)[0]) {
              const elm = document.getElementsByClassName(getElm)[0]
              if (this.alertPosition === 'inline') {
                if (elm.previousSibling) {
                  elm.previousSibling.scrollIntoView()
                } else {
                  elm.scrollIntoView()
                }
              } else {
                elm.scrollIntoView()
              }
              clearInterval(checkElm)
            }
          }.bind(this),
          100
        )
      }
      if (this.persistFor > 0) {
        setTimeout(
          function() {
            this.isActiveData = false
          }.bind(this),
          this.persistFor * 1000
        )
      }
    }
  }
}
</script>

<style>
.nugget-error {
  font-size: 16px;
  margin: 10px 0;
  color: red;
}
.nugget-warning {
  font-size: 16px;
  margin: 10px 0;
  color: orange;
}
</style>
