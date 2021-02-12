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
</style>
