<template>
  <div>
    <div id="countUpEl"></div>

    <div class="btn-group" id="btnAction">
      <button type="button" class="btn btn-success btn-lg" @click="startCount">{{ displayName }}</button>
      <button type="button" class="btn btn-warning btn-lg" @click="reset">ReSet</button>
      <button type="button" class="btn btn-info btn-lg" @click="pauseRresume">Pause/Resume</button>
    </div>
  </div>
</template>

<script>
import countUp from "countup.js";
export default {
  props: ["opts"],
  data() {
    return {
      countUp    : null,
      defaultOpts: {
        element : "countUpEl",
        startVal: 0,
        endVal  : 100,
        decimals: 0,
        duration: 2
      },
      displayName: "start"
    };
  },
  mounted() {
    this.InitCountUp();
  },
  methods: {
    /**
     * TODO: 计时器初始化
     */
    InitCountUp() {
      this.defaultOpts.startVal = 
        this.opts.startVal || this.defaultOpts.startVal;
      this.defaultOpts.endVal   = this.opts.endVal || this.defaultOpts.endVal;
      this.defaultOpts.decimals = 
        this.opts.decimals || this.defaultOpts.decimals;
      this.defaultOpts.duration = 
        this.opts.duration || this.defaultOpts.duration;
      this.countUp = new countUp(
        this.defaultOpts.element,
        this.defaultOpts.startVal,
        this.defaultOpts.endVal,
        this.defaultOpts.decimals,
        this.defaultOptsduration
      );
    },
    startCount() {
      this.countUp && this.countUp.start();
      this.displayName = "stop";
    },
    reset() {
      this.countUp && this.countUp.reset();
    },
    pauseRresume() {
      this.countUp && this.countUp.pauseResume();
    }
  }
};
</script>

<style scopted>
#countUpEl {
  color        : red;
  font-size    : 50px;
  font-weight  : 900;
  border       : 1px solid #ccc;
  border-radius: 10px;
  padding      : 10px;
  width        : 30%;
  margin       : 0 auto;
  margin-top   : 20px;
}
#btnAction {
  margin    : 0 auto;
  margin-top: 20px;
  
}
</style>