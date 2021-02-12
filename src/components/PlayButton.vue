<template>
  <button v-on:click="launchGame">Lancer la partie</button>
</template>

<script>
export default {
  name: "PlayButton",
  methods: {
    launchGame() {
      this.$emit("launch-game");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
