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
button {
    background-color: #F8F8F8;
    margin: 20px;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.20);
    transition: .2s;
    border: 0px;
    cursor: pointer;
    outline: none;
}

button:hover {
    color: red;
    box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.20);
    transition: .2s;
}
</style>
