<template>
  <div id="home">
    <h3>Bienvenue dans votre liste de jeux !</h3>

    Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum quae beatae, eos voluptatem asperiores, blanditiis vel aliquam provident animi in neque sunt deleniti nulla perferendis praesentium excepturi laudantium, inventore enim.
    <router-view id="router-outlet"></router-view>
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
#router-outlet {
  padding-top: 10px;
}
</style>
