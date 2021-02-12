<template>
  <span>Level {{ level }}</span>
</template>

<script>
export default {
  name: "Level",
  data: function () {
    return {
      level: 1,
    };
  },
  methods: {
    levelUp() {
      this.level++;
    },
    restartLevel() {
      this.level = 1;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
