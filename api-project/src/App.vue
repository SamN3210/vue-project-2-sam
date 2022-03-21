<template>
  <nav>
    <div class="flex-container">
      <button><router-link to="/">Home</router-link></button>
      <button><router-link to="/about">About</router-link></button>
    </div>
  </nav>
  <router-view/>
</template>

<style>
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
  
}
</style>
