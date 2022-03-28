<template>
    <router-link :to="pokemonpath" class="router-link">
        <div class="pokemon-card">
            <h1>{{pokemon.name}}</h1>
            <h2>{{index + 1}}</h2>
        </div>
    </router-link>
</template>

<script>
export default {
    props: {
        pokemon: Object,
        index: Number,
    },
    computed: {
        pokemonpath: function() {
            return `/PokemonInfo/${this.index +1}`
        }
    }
}
</script>

<style scoped>
.router-link,
.router-link:visited,
.router-link:link {
    background-color: aliceblue;
    color: black;
    width: 22%;
    border-radius: 10px;
    margin: 1rem;
    padding: 1rem 1rem;
}
h1{
    text-transform: capitalize;
}
</style>