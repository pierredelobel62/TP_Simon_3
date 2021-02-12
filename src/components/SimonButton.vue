<template>
  <button v-bind:class="[data.name, data.active ? 'active': '']" v-on:click="clickButton(data)"></button>
</template>

<script>
export default {
  name: 'SimonButton',
  props: {
    data: Object
  },
  methods: {
        clickButton(value) {
            value.active = true;
            value.sound.play();
            setTimeout(() => {
                value.active = false;
            }, 500);
            this.$emit('click', value);
        },
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#simon #buttons button {
  width: 48%;
  margin: 1%;
  text-align: center;
  outline: none;
  background-color: white;
  padding: 100px;
}
.red {
  border: 2px solid red;
}
.red.active {
  background-color: red !important;
}
.yellow {
  border: 2px solid yellow;
}
.yellow.active {
  background-color: yellow !important;
}
.purple {
  border: 2px solid purple;
}
.purple.active {
  background-color: purple !important;
}
.blue {
  border: 2px solid blue;
}
.blue.active {
  background-color: blue !important;
}
</style>
