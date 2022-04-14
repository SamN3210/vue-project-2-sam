<template>
  <head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Mukta:wght@300;400;600&display=swap" rel="stylesheet">
  </head>
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
html, body, * {
  font-family: 'Mukta', sans-serif;
}
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
