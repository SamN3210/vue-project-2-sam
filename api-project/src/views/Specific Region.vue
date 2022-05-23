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
        let baseurl = "https://pokeapi.co/api/v2/pokemon?"
        const response = await fetch(baseurl.concat("limit=151&offset=151"));
        const data = await response.json();
        this.pokemons = data.results;
        console.log(this.pokemons);
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
