<template>
  <div class="about">
    <h1>Search</h1>
    <form id="app" @submit="fetchData">
        <p>
            <label for="name">Name</label>
            <input
            id="name"
            v-model="name"
            type="text"
            name="name"
            >
        </p>
        <p>
            <input
            type="submit"
            value="Submit"
            >
        </p>
    </form>
    <div v-if="dataReturned">
      <h1>{{PokemonData.name}}</h1>
      <h1>#{{PokemonData.id.toString().padStart(3, "0")}}</h1>
      <img class="sprite" :src="spriteFront" :alt="altText"/>
      <u1 class="types">
        <PokemonTypes 
        v-for="type in PokemonData.types" :key="type" 
        :type="type.type.name"/>
      </u1>
      <u1 class="stats">
        <li v-for="stat in PokemonData.stats" :key="stat" class="poke-stat">
          <div :style=backgroundColor>{{stat.stat.name}}</div>
          <div :style=backgroundColor>{{stat.base_stat}}</div>
        </li>
      </u1>
    </div>
    <h1 v-else>Enter a correct Pokemon Name.</h1>
  </div>
</template>

<script>
// @ is an alias to /src
import PokemonTypes from "../components/PokemonTypes.vue"
export default {
  name: 'SearchView',
  components: {
    PokemonTypes
  },
  data(){
      return{
          name: null,
          PokemonData: {},
          dataReturned: false,
          colors: {
                grass: "#d5faa3",
                fire: "#ffa83e",
                water: "#0077b6",
                electric: "#ffd000",
                bug: "#c9d019",
                dark: "#343a40",
                fairy: "#faa5e4",
                poison: "#a755c2",
                fighting: "#a35200",
                ice: "#caf0f8",
                psychic: "#ff4d80",
                ghost: "#8b728e",
                flying: "#c2dfe3",
                steel: "#7c90a0",
                ground: "#7f4f24",
                rock: "#d4a276",
                dragon: "#6730ec",
                normal: "#e9ecef",
          }
      }
  },
  methods: {
      fetchData: async function(e){
        try {
            e.preventDefault();
            const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.name.toLowerCase()}`);
            const data = await response.json();
            this.PokemonData = data;
            console.log(this.PokemonData);
            this.dataReturned = true;
            return this.PokemonData;
        }
        catch (error) {
            console.log("error");
            this.dataReturned = false;
        }
    },
  },
  computed: {
    spriteFront: function(){
      return `https://assets.pokemon.com/assets/cms2/img/pokedex/full/${this.PokemonData.id.toString().padStart(3, "0")}.png`;
    },
    altText: function(){
      return this.PokemonData.name
    }
  }
}
</script>

<style scoped>
h1{
    text-transform: capitalize;
}
.sprite{
  height: 20vh;
}
label{
  color:white;
}
h3{
  width:10%;
  height: 2rem;
  padding: 1rem;
  color: black;
  text-transform: capitalize;
}
.types{
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
  align-content: center;
}
.poke-stat{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  flex-wrap: wrap;
  align-content: center;
}
li{
  color: white;
  text-transform: capitalize;
}
</style>