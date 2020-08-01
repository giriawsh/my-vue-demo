<template>
  <div class="container">
    <div class="tools">
      <div>
        <input type="color" v-model="color1"/>
        <input type="text" v-model="color1"/>
      </div>
      <div>
        <div class="vertical-range">
          <input type="range" :min="min" :max="max" v-model="steps" xorient="vertical" style="color: #000000;"/>
        </div>
        <div class="steps">{{visualSteps}} {{visualStepsLabel}}</div>
      </div>
      <div>
        <input type="color" v-model="color2"/>
        <input type="text" v-model="color2"/>
      </div>

      <div class="colors">
        <div class="color" v-for="color in colors" :style="setStyles(color)">&nbsp;{{colorName(color)}}</div>
      </div>
    </div>
  </div>
</template>
<script>
  import {vueMixinColorFunctions} from '../mixin/vueMixinColorFunctions'

  export default {
    name: 'colorTab',
    mixins: [vueMixinColorFunctions],
    data() {
      return {
        min: 3,
        max: 27,
        delta: 10,
        steps: 10,
        color1: '#0ebeff',
        color2: '#ff42b3',
      }
    },
    computed: {
      colors() {
        return this.interpolateColors(this.color1, this.color2, this.steps)
      },
      visualSteps() {
        return (this.steps - 2)
      },
      visualStepsLabel() {
        return (this.visualSteps === 1 ? 'step' : 'steps')
      },
    },
    methods: {
      adjust(color) {
        const hex = this.rgbToHex(color[0], color[1], color[2])
        return this.foregroundAdjust(hex)
      },
      setStyles(color) {
        return `background: rgb(${color}); color: ${this.adjust(color)}`
      },
      colorName(color) {
        return this.rgbArrayToHex(color);
      },
    }
  }
</script>
<style scoped>
  .tools {
    flex: 1;
    padding: 2em;
    color: #000;
  }

  .tools div {
    display: flex;
    position: relative;
  }

  .tools div + div {
    margin-top: .5em;
  }

  .vertical {
    display: flex;
    align-items: center;
    width: 10em;
    height: 10em;
    -webkit-transform: rotate(-90deg);
    transform: rotate(-90deg);
  }

  .tools .steps {
    position: absolute;
    top: 50%;
    left: 6em;
    -webkit-transform: translate(0, -50%);
    transform: translate(0, -50%);
    color: #000000;
    padding: 0;
    margin: 0;
  }

  .colors {
    flex: 2;
    display: flex;
    flex-direction: column;
    font-size: .85em;
  }

  .colors .color {
    /*flex: 1;*/
    display: flex;
    align-items: center;
    padding: 0 1em;
    transition: 300ms linear;
    height: 50px;
    animation: bounceInLeft 1s cubic-bezier(0.215, 0.610, 0.355, 1.000)
  }
  @keyframes bounceInLeft {
    0% {
      opacity: 0;
      transform: translate3d(-3000px, 0, 0);
    }
    60% {
      opacity: 1;
      transform: translate3d(25px, 0, 0);
    }
    75% {
      transform: translate3d(-10px, 0, 0);
    }
    90% {
      transform: translate3d(5px, 0, 0);
    }
    100% {
      transform: none;
    }
  }


  .vertical-range {
    display: flex;
    align-items: center;
    width: 9em;
    height: 9em;
    -webkit-transform: rotate(-90deg);
    transform: rotate(-90deg);
    color: #000;
  }

  .steps-control {
    width: 10em;
    height: 10em;
  }

  /*.steps-control .ring {*/
  /*  -webkit-transform: scale(calc(var(--size) / 40));*/
  /*  transform: scale(calc(var(--size) / 40));*/
  /*  width: 100%;*/
  /*  box-shadow: 0 0 0 .2em;*/
  /*  border-radius: 5em;*/
  /*  -webkit-transform: 300ms linear;*/
  /*  transform: 300ms linear;*/
  /*}*/

  input {
    margin: 0;
    padding: 0 .5em;
    font-size: inherit;
    font-family: inherit;
    border: none;
    width: 7em;
    outline: none;
    border-radius: 0 1em 1em 0;
  }

  input[type=color] {
    padding: 0;
    width: 2em;
    height: 2em;
    border-radius: 1em 0 0 1em;
  }

  input[type=color]::-webkit-color-swatch {
    border: none;
    border-radius: 1em;
  }

  input[type=color]::-webkit-color-swatch-wrapper {
    padding: .25em;
    border-radius: 1em;
  }

  input[type=range] {
    -webkit-appearance: none; /*清除系统默认样式*/
    width: 100%;
    background: -webkit-linear-gradient(#ddd, #ddd) no-repeat, #ddd; /*设置左边颜色为#61bd12，右边颜色为#ddd*/
    background-size: 75% 100%; /*设置左右宽度比例*/
    height: 5px; /*横条的高度*/
  }

  /*拖动块的样式*/
  input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none; /*清除系统默认样式*/
    height: 26px; /*拖动块高度*/
    width: 26px; /*拖动块宽度*/
    background: #fff; /*拖动块背景*/
    border-radius: 50%; /*外观设置为圆形*/
    border: solid 1px #ddd; /*设置边框*/
  }
  @supports (-webkit-backdrop-filter: blur(2em)) {
    input[type=color] {
      display: none;
    }

    input {
      border-radius: 1em;
      padding: .25em .5em;
      width: 9em;
    }
  }

  /**,*/
  /**::before,*/
  /**::after {*/
  /*  box-sizing: border-box;*/
  /*}*/

  .container {
    display: flex;
    width: 100%;
    height: 100%;
    overflow: hidden;
    background: radial-gradient(ellipse at bottom, #F5F5F5 0%, #ffffff 100%);
    color: rgba(100, 200, 255, 0.7);
    font-family: 'Dosis', sans-serif;
    /*font-size: 8rem;*/
  }

  @supports (-webkit-backdrop-filter: blur(2em)) {
    input[type=color] {
      display: none;
    }

    input {
      border-radius: 1em;
      padding: .25em .5em;
      width: 9em;
    }
  }
</style>
