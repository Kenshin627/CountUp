<template>
  <div id="app">
    <count-up :opts="options"></count-up>
  </div>
</template>

<script>
import countUp from './components/countUp.vue'
export default {
  data() {
    return {
      options: {
         startVal: 0,
         endVal  : 100,
         decimals: 0,
         duration: 2
      }
    }
  },
  components: {
    "countUp": countUp
  }
}
</script>

<style>

</style>
