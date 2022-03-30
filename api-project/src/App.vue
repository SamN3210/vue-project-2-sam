<template>
  <nav>
    <div class="flex-container">
      <button><router-link to="/">Home</router-link></button>
      <button><router-link to="/regions">Pokedex</router-link></button>
      <button><router-link to="/search">Search Pokemon</router-link></button>
    </div>
  </nav>
  <router-view/>
</template>

<style>
#app {
  text-align: center;
}
body {
  background-color: #8EA4D2;
}
nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

.flex-container{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
