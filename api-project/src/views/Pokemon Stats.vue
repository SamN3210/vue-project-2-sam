<template>
  <div>
    <h1>This is a stats page</h1>
    <div v-if="dataReturned">
      <h2>{{PokemonData.name}}</h2>
      <h2>#{{PokemonData.id.toString().padStart(3, "0")}}</h2>
      <img class="sprite" :src="spriteFront" alt=""/>
    </div>
    <h2 v-else></h2>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'PokemonInfo',
  components: {
  },
  data(){
      return{
          PokemonData: {},
          dataReturned: false,
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
    }
  }
}
</script>

<style scoped>
h2{
    text-transform: capitalize;
}
.sprite {
  height: 20vh;
}
</style>