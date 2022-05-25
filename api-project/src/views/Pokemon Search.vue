<template>
  <div class="about">
    <h1>This is a search page</h1>
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
      <h2>{{PokemonData.name}}</h2>
      <h2>{{PokemonData.id}}</h2>
      <img class="sprite" :src="spriteFront" alt=""/>
    </div>
    <h2 v-else>Enter a correct Pokemon Name.</h2>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'SearchView',
  components: {
  },
  data(){
      return{
          name: null,
          PokemonData: {},
          dataReturned: false,
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
    }
  }
}
</script>

<style scoped>
h2{
    text-transform: capitalize;
}
.sprite{
  height: 20vh;
}
</style>