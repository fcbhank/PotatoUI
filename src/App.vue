<template>
  <TomatoClock></TomatoClock>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import HelloWorld from './components/TomatoClock/TomatoClock';

@Options({
  components: {
    TomatoClock,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">

</style>
