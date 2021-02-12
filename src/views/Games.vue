<template>
  <div id="container">
    <div id="header">
      <h3>Mes jeux</h3>
    </div>
    <div id="body">
      <ul>
        <li><router-link to="/simon">Jeu du Simon</router-link></li>
        <li><router-link to="/simon">Jeu du Simon</router-link></li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
li {
    display: inline;
}
a {
    background-color: #F8F8F8;
    margin: 20px;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.20);
    transition: .2s;
}

#body {
    padding-top: 10px;
}

a {
    color: black;
    text-decoration: none;
    transition: .2s;
}

li:hover a {
    color: red;
    box-shadow: 0px 0px 10px 0px rgba(0,0,0,0.20);
    transition: .2s;
}

</style>