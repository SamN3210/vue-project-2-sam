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
          name: "",
          PokemonData: {},
      }
  },
  methods: {
      fetchData: async function(){
        try {
            const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.name}`);
            const data = await response.json();
            this.PokemonData = data;
            return this.PokemonData;
        }
        catch (error) {
            console.log("error");
        }
    }
  },
}
</script>