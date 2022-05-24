<template>
  <div class="about">
    <h1>This is a specific region page</h1>
    <div class="flex-container">
      <SpecificCard
      v-for="(pokemon, index) in pokemons"
      :key="pokemon.name"
      :pokemon="pokemon"
      :index="index"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import SpecificCard from "../components/SpecificCard.vue"
export default {
  name: 'SpecificRegionView',
  components: {
    SpecificCard,
  },
  data(){
    return{
      pokemons: [],
    }
  },
  methods:{
    fetchData: async function(){
      try {
        const baseurl = "https://pokeapi.co/api/v2/pokemon?";
        let path = this.pathname || window.location.pathname;
        console.log(path);
        if (path === "/pokemons/kanto") {
          let region = "limit=151&offset=0"
          const response = await fetch(baseurl.concat(region));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
        }
        if (path === "/pokemons/johto") {
          let region = "limit=100&offset=151"
          const response = await fetch(baseurl.concat(region));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
        }
        if (path === "/pokemons/hoenn") {
          let region = "limit=135&offset=251"
          const response = await fetch(baseurl.concat(region));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
        }
        if (path === "/pokemons/sinnoh") {
          let region = "limit=107&offset=386"
          const response = await fetch(baseurl.concat(region));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
        }
        if (path === "/pokemons/unova") {
          let region = "limit=156&offset=493"
          const response = await fetch(baseurl.concat(region));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
        }
        if (path === "/pokemons/kalos") {
          let region = "limit=72&offset=649"
          const response = await fetch(baseurl.concat(region));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
        }
        if (path === "/pokemons/alola") {
          let region = "limit=86&offset=721"
          const response = await fetch(baseurl.concat(region));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
        }
        if (path === "/pokemons/galar") {
          let region = "limit=89&offset=809"
          const response = await fetch(baseurl.concat(region));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
        }
      }
      catch (error) {
        console.log("error");
      }
    },
  },
  created: function (){
    this.fetchData();
  },
}
</script>

<style scoped>
.flex-container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
