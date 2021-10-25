<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    };
  },
  mounted() {
    //  this will fire only when mounted to the DOM
    setTimeout(() => {
      this.showBlock = true,
        this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);

    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
    }
  }
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 20px;
  color: green;
  text-align: center;
  background: aquamarine;
  padding: 100px 0;
  margin: 40px auto;

}
</style>
