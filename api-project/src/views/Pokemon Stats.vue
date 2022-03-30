<template>
  <div class="stats-container">
    <h1>This is a stats page</h1>
    <h2>{{PokemonData.name}}</h2>
    <img :src="spriteFront" alt=""/>
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
            return this.PokemonData;
        }
        catch (error) {
            console.log("error");
        }
    }
  },
  computed: {
    spriteFront: function(){
      return this.PokemonData.sprites.front_default;
    }
  }
}
</script>

<style scoped>
.stats-container{
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    flex-wrap: wrap;
}
h2{
    text-transform: capitalize;
}
</style>