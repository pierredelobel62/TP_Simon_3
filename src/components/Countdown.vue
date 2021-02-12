<template>
  <h1 v-if="countdown >= 0">{{ countdown }}</h1>
</template>

<script>
export default {
  name: "Countdown",
  data: function () {
    return {
      countdown: 5,
    };
  },
  methods: {
    launch() {
      const that = this;
      var interval = setInterval(function () {
        that.countdown--;
        if (that.countdown == 0) {
          clearInterval(interval);
          that.countdown--;
          that.$emit("finish");
        }
      }, 1000);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
