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
:root {
  --light-grass: #d5faa3;
  --dark-grass: #28e81a;
  --light-fire: #ffa83e;
  --dark-fire: #dc2f02;
  --light-water: #8ecae6;
  --dark-water: #0077b6;
  --light-electric: #ffe97f;
  --dark-electric: #ffd000;
  --light-bug: #c9d019;
  --dark-bug: #618b25;
  --light-dark: #6c757d;
  --dark-dark: #343a40;
  --light-fairy: #ffc8dd;
  --dark-fairy: #faa5e4;
  --light-poison: #ca86f4;
  --dark-poison: #a755c2;
  --light-fighting: #ffb870;
  --dark-fighting: #a35200;
  --light-ice: #caf0f8;
  --dark-ice: #0096c7;
  --light-psychic: #ff4d80;
  --dark-psychic: #c91b7a;
  --light-ghost: #8b728e;
  --dark-ghost: #694873;
  --light-flying: #c2dfe3;
  --dark-flying: #9db4c0;
  --light-steel: #c9c9c9;
  --dark-steel: #7c90a0;
  --light-ground: #bb9457;
  --dark-ground: #7f4f24;
  --light-rock: #d4a276;
  --dark-rock: #6f4518;
  --light-dragon: #cddafd;
  --dark-dragon: #6730ec;
  --light-normal: #e9ecef;
  --dark-normal: #adb5bd;
  --main-white: ##f0f0f0;
  --main-red: #ff686b;
  --main-black: #222224;
  --main-gray: #495057;
}

/* Define Font Sizes */
h1 {
  font-size: var(--h2);
  color:white;
}
h1,
h2,
h3,
h4,
h5 {
  text-align: center;
}
#app {
  text-align: center;
}
body {
  background-color: var(--main-gray);
}
nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: white;
}

nav a.router-link-exact-active {
  color: var(--main-red);
}

.flex-container{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  flex-wrap: wrap;
}
button{
    width: 15vw;
    margin: 1rem;
    background-color: var(--main-black);
    color:white;
    height: 10vh;
    border-radius: 10px;
}
</style>
