<template>
  <div class="about">
    <h1>This is a region page</h1>
    <div class="button-container">
      <RegionButton
      v-for="region in regions"
      :key="region"
      :region="region"
      />
    </div>
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
import RegionButton from "../components/RegionButton.vue"
export default {
  name: 'RegionView',
  components: {
    PokemonCard,
    RegionButton,
  },
  data(){
    return{
      pokemons: [],
      regions: ["Kanto", "Johto", "Hoenn", "Sinnoh", "Unova", "Kalos", "Alola", "Galar", "All"],
    }
  },
  methods:{
    fetchData: async function(){
      try {
        const response = await fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0");
        const data = await response.json();
        this.pokemons = data.results;
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