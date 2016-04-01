<template>
  <div>
  <div class="slider" :style="slider">
    <div class="track" :style="track"></div>
    <div class="untrack" :style="untrack"></div>
    <input type="range" min="0" max="100" v-model="value">
  </div>
  <div class="output"><output>{{value}}</output></div>
  </div>
</template>
<script>
export default {
  props: {
    value: {
      type: Number,
      default: 0
    },
    width: {
      type: Number,
      default: 200
    }
  },

  computed: {
    slider () {
      return {
        width: this.width + 'px'
      }
    },
    track () {
      let trackWidth = this.value
      return {
        width: trackWidth + 'px'
      }
    },
    untrack () {
      return {
        left: this.value + 'px',
        width: 100 - this.value + 'px'
      }
    }
  }
}
</script>

<style>
.slider {
  position: relative;
}
input[type="range"] {
  position: absolute;
  top: 0;
  left: 0;
  width: 100px;
  appearance: none;
  background: transparent;
  height: 5px;
  border: none;
  border-radius: 1.25%;
  z-index: 2;
}
input:focus {
  outline: none
}
input[type=range]::-webkit-slider-thumb {
  -webkit-appearance: none;
  border: 1px solid #000000;
  height: 16px;
  width: 16px;
  border-radius: 50%;
  background: #ffffff;
  cursor: pointer;
  border: 0.5px solid #d5d5d5;
  box-shadow: 0 1px 1px rgba(0,0,0,10),
              0 2px 2px rgba(0,0,0,30);
  /* margin-top: -14px;  */
}
.track {
  position: absolute;
  top: 0;
  left: 0;
  height: 5px;
  background: #3c98fc;
  border-radius: 2px;
  margin: 2px;
  z-index: 1;
}
.untrack {
  position: absolute;
  top: 0;
  height: 5px;
  background: #b3b3b3;
  z-index: 0;
  margin: 2px;
  border-radius: 2px;
}
output {
  position: absolute;
  right: 0;
  top: 0;
}
</style>
