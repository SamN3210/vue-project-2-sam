<template>
  <div>
    <div v-if="dataReturned">
      <h1>{{PokemonData.name}}</h1>
      <h1>#{{PokemonData.id.toString().padStart(3, "0")}}</h1>
      <img class="sprite" :src="spriteFront" alt="PokemonSprite"/>
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
    <h2 v-else></h2>
  </div>
</template>

<script>
// @ is an alias to /src
import PokemonTypes from "../components/PokemonTypes.vue"
export default {
  name: 'PokemonInfo',
  components: {
    PokemonTypes
  },
  data(){
      return{
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
  mounted: function (){
    this.fetchData();
  },
  methods: {
      fetchData: async function(){
        try {
            const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.$route.params.id}`);
            const data = await response.json();
            this.PokemonData = data;
            console.log(this.PokemonData);
            console.log(this.PokemonData.sprites.front_default)
            this.dataReturned = true;
            return this.PokemonData;
        }
        catch (error) {
            console.log("error");
            this.dataReturned = true;
        }
    }
  },
  computed: {
    spriteFront: function(){
      return `https://assets.pokemon.com/assets/cms2/img/pokedex/full/${this.PokemonData.id.toString().padStart(3, "0")}.png`;
    },
    backgroundColor:function(){
                return "background-color: " + this.colors[`${this.type}`];
            }
  }
}
</script>

<style scoped>
h1{
    text-transform: capitalize;
}
.sprite {
  height: 20vh;
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