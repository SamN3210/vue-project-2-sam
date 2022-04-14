<template>
  <div class="about">
    <h1>This is a region page</h1>
    <div class="flex-container">
      <PokemonCard
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
import PokemonCard from "../components/PokemonCard.vue"
export default {
  name: 'SpecificRegionView',
  components: {
    PokemonCard,
  },
  data(){
    return{
      pokemons: [],
    }
  },
  methods:{
    fetchData: async function(){
      try {
        const response = await fetch("https://pokeapi.co/api/v2/pokedex/national");
        const data = await response.json();
        this.pokemons = data.pokemon_entries;
        console.log(this.pokemons);
      }
      catch (error) {
        console.log("error");
      }
    }
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
