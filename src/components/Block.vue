<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return { showBlock: false, timer: null, reactionTime: 0 };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      });
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
};
//   updated() {
//     console.log("component updated");
//   },
//   unmounted() {
//     console.log("unmounted");
//   },
// };
</script>

<style>
.block {
  width: 400px;
  height: 300px;
  background: burlywood;
  margin: 50px auto;
  text-align: center;
}
</style>
