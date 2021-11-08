<template>
  <div class="scale-box" :style="getDegree">
    <div class="scale"></div>
    <span class="number">{{ this.scale }}</span>
  </div>
</template>

<script>
export default {
  name: "TomatoClockScale",
  props: {
    scale: {
      type: Number,
      default: 0
    }
  },
  computed: {
    getDegree() {
      return {
        '--degree': this.scale * 30 + 'deg',
        '--degree-reverse': 360 - this.scale * 30 + 'deg'
      }
    }
  }
}
</script>

<style scoped lang="scss">
.scale-box {
  width: 2px;
  height: 150px;
  display: inline;

  position: absolute;

  top: 0;
  left: 145px;

  transform-origin: center bottom;

  transform: rotate(var(--degree));

  .scale {
    display: block;
    width: 2px;
    height: 10px;
    box-shadow: 1px 1px 1px #9D958F inset, -1px -1px 1px var(--clock-background-color) inset;
    border-radius: 1px;
  }

  .number {
    display: block;
    width: 2rem;
    height: 1em;

    position: absolute;
    padding-left: 10px;

    transform: rotate(var(--degree-reverse));
  }
}
</style>
