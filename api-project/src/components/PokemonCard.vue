<template>
    <router-link :to="pokemonPath" class="router-link">
        <div class="pokemon-card">
            <h1>{{pokemon.pokemon_species.name}}</h1>
            <h1>#{{pokemonNumber.toString().padStart(3, "0")}}</h1>
            <img class="sprite" :alt="altText" :src="iconSprite"/>
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
        pokemonPath: function() {
            return `/pokemoninfo/${this.index +1}`
        },
        pokemonNumber: function() {
            return this.index + 1
        },
        iconSprite: function() {
            return `https://img.pokemondb.net/sprites/sword-shield/icon/${this.pokemon.pokemon_species.name}.png`
        },
        altText: function() {
            return this.pokemon.pokemon_species.name
        }
    }
}
</script>

<style scoped>
.router-link,
.router-link:visited,
.router-link:link {
    background-color: var(--main-black);
    color: white;
    width: 10%;
    border-radius: 10px;
    margin: 1rem;
    padding: 1rem 1rem;
}
h1{
    text-transform: capitalize;
}
</style>