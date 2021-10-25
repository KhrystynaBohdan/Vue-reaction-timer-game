<template>
  <div class="block" v-if="showBlock">
    click me
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false
    };
  },
  mounted() {
    //  this will fire only when mounted to the DOM
    console.log("component mounted");
    setTimeout(() => {
      this.showBlock = true
      console.log (this.delay)
    }, this.delay)
  },
  updated() {
    //  this will fire only when data in component updated
    console.log('components updated')
  },
  unmounted() {
    //  this will fire only when component unmounted from the Dom, is also good when we are working with vue router
    console.log('component unmounted')
  }
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 20px;
  color: white;
  text-align: center;
  background: aquamarine;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
