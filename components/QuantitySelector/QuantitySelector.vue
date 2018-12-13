<template>
  <div>
    <div class="nugget-quantity-label">
      <strong>Quantity: {{ countData }}</strong>
    </div>
    <div class="nugget-quantity-counter">
      <div @click="decrement">
        <svg
          v-if="stepInterval === 1"
          :width="iconDimensions"
          :height="iconDimensions"
          viewBox="0 0 24 24"
        >
          <g>
            <path
              :fill="minusIconColor"
              d="M64 0 M2 11 L2 13 L22 13 L22 11 Z" />
          </g>
        </svg>
        <div
          v-else
          :style="{color: minusIconColor, fontSize: iconDimensions + 'px'}"
          class="nugget-quantity-step"
        >-{{ stepInterval }}</div>
      </div>
      <input
        v-if="isCountEditable"
        :min="count"
        :max="maxCount"
        v-model.number="countData"
        type="number"
        @blur="adjustCount"
        @keypress="restrictChars($event)"
      >
      <div v-else>{{ countData }}</div>
      <div @click="increment">
        <svg
          v-if="stepInterval === 1"
          :width="iconDimensions"
          :height="iconDimensions"
          viewBox="0 0 24 24"
        >
          <g>
            <path
              :fill="plusIconColor"
              d="M 11 2 L 11 11 L 2 11 L 2 13 L 11 13 L 11 22 L 13 22 L 13 13 L 22 13 L 22 11 L 13 11 L 13 2 Z" />
          </g>
        </svg>
        <div
          v-else
          :style="{color: plusIconColor, fontSize: iconDimensions + 'px'}"
          class="nugget-quantity-step"
        >+{{ stepInterval }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'QuantitySelector',
  props: {
    count: {
      type: Number,
      default: 1
    }, // Makes sense to have default product count value
    maxCount: {
      type: Number,
      default: 6
    }, // maxCount makes sense when you have a restriction on the max quantity for a product
    iconDimensions: {
      type: Number,
      default: 15
    },
    stepInterval: {
      type: Number,
      default: 1
    },
    minusIconFillColor: {
      type: String,
      default: '#000'
    },
    plusIconFillColor: {
      type: String,
      default: '#000'
    },
    isCountEditable: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      countData: this.count
    }
  },
  computed: {
    minusIconColor: function() {
      return this.countData === this.count ? '#CCC' : this.minusIconFillColor
    },
    plusIconColor: function() {
      return this.countData === this.maxCount ? '#CCC' : this.plusIconFillColor
    }
  },
  methods: {
    decrement: function() {
      if (this.countData > this.count) {
        this.countData -= this.stepInterval
      }
    },
    increment: function() {
      if (this.countData < this.maxCount) {
        this.countData += this.stepInterval
      }
    },
    adjustCount: function() {
      if (this.countData > this.maxCount) {
        this.countData = this.maxCount
      } else if (this.countData < this.count) {
        this.countData = this.count
      } else if (this.countData > this.count && this.countData < maxCount) {
        this.countData = this.countData
      } else {
        if (isNaN(Number(this.countData))) {
          this.countData = this.count
        }
      }
    },
    restrictChars: function($event) {
      if (
        $event.charCode === 0 ||
        /\d/.test(String.fromCharCode($event.charCode))
      ) {
        return true
      } else {
        $event.preventDefault()
      }
    }
  }
}
</script>

<style>
.nugget-quantity-counter {
  display: inline-flex;
}
.nugget-quantity-label {
  margin-bottom: 10px;
}
.nugget-quantity-counter div:first-child {
  border: solid 1px #ccc;
  border-radius: 5px 0px 0px 5px;
}
.nugget-quantity-counter div:nth-child(2) {
  border-top: solid 1px #ccc;
  border-bottom: solid 1px #ccc;
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 30px;
}
.nugget-quantity-counter input[type='number'] {
  border-top: solid 1px #ccc;
  border-bottom: solid 1px #ccc;
  border-left: none;
  border-right: none;
  text-align: center;
  width: 30px;
  padding: 12px;
  margin: 0;
  font-size: 16px;
  -moz-appearance: textfield;
}
.nugget-quantity-counter input[type='number']::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.nugget-quantity-counter .nugget-quantity-step {
  border: none !important;
  font-size: 16px;
}
.nugget-quantity-counter div:last-child {
  border: solid 1px #ccc;
  border-radius: 0px 5px 5px 0px;
}
.nugget-quantity-counter > div {
  cursor: pointer;
  padding: 12px;
  min-width: 20px;
  width: auto;
  text-align: center;
  position: relative;
}
.nugget-quantity-counter > div > svg {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
