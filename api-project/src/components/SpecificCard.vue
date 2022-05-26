<template>
    <router-link :to="pokemonPath" class="router-link">
        <div class="pokemon-card">
            <h1>{{pokemon.name}}</h1>
            <h1>#{{this.numberPath.toString().padStart(3, "0")}}</h1>
            <img class="sprite" :src="iconSprite" :alt="altText"/>
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
            return `/pokemoninfo/${this.numberPath}`
        },
        numberPath: function() {
            let str = this.pokemon.url
            let arr = str.split('/');
            return arr[arr.length-2]
        },
        iconSprite: function() {
            return `https://img.pokemondb.net/sprites/sword-shield/icon/${this.pokemon.name}.png`
        },
        altText: function() {
            return this.pokemon.name
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