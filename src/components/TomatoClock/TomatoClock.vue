<template>
  <div class="clock" :style="styleClock">
    <div class="inner-boarder">
      <div class="scales">
        <div :key="scale" v-for="scale of 12">
          <TomatoClockScale :scale=scale></TomatoClockScale>
        </div>
      </div>
      <div class="pointers">
        <div class="pointer-hours"></div>
        <div class="pointer-minutes"></div>
        <div class="pointer-seconds"></div>
      </div>
    </div>
    <div class="wave"></div>
  </div>
</template>

<script>
import TomatoClockScale from "./TomatoClockScale";
export default {
  name: "TomatoClock",
  components: {TomatoClockScale},
  props: {
    size: {
      type: Number,
      default: 300
    },
    backgroundColor: {
      type: String,
      default: '#66ccff'
    }
  },
  computed: {
    styleClock() {
      return {
        '--clock-size': this.size + 'px',
        '--clock-background-color': this.backgroundColor,
        '--clock-radius': (this.size - 10) / 2 + 'px',
        '--length-log2E': ((this.size - 10) / 2) / Math.LOG2E + 'px',
      }
    }
  },
}
</script>

<style scoped lang="scss">
.clock {
  width: var(--clock-size);
  height: var(--clock-size);
  border-radius: 50%;
  box-shadow: 5px 5px 10px var(--clock-background-color), -4px -4px 8px #fff;
}

.inner-boarder {
  width: calc(var(--clock-size) - 10px);
  height: calc(var(--clock-size) - 10px);
  position: relative;
  left: 5px;
  top: 5px;
  box-shadow: -3px -3px 6px #fff inset, 3px 3px 6px var(--clock-background-color) inset;
  border-radius: 50%;
}


  span.number {
    display: block;
    position: relative;

  }





.pointers {

}


.wave {
  width: 150px;
  height: 150px;
  position: absolute;
  left: 85px;
  top: 85px;
  box-shadow: 3px 3px 9px var(--clock-background-color), -3px -3px 9px #fff;
  border-radius: 50%;
  filter: blur(1px);
  animation: wave-move 4s infinite linear;
}

@keyframes wave-move {
  0% {
    transform: scale(0.5);
  }
  50% {
    transform: scale(1);
    opacity: 1;
  }
  100% {
    transform: scale(1.7);
    opacity: 0;
  }
}
</style>
