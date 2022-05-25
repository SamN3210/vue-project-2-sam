<template>
    <router-link :to="pokemonPath" class="router-link">
        <div class="pokemon-card">
            <h2>{{pokemon.name}}</h2>
            <h3>#{{this.numberPath.toString().padStart(3, "0")}}</h3>
            <img class="sprite" :src="iconSprite"/>
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
        }
    }
}
</script>

<style scoped>
.router-link,
.router-link:visited,
.router-link:link {
    background-color: #6279B8;
    color: black;
    width: 10%;
    border-radius: 10px;
    margin: 1rem;
    padding: 1rem 1rem;
}
h2{
    text-transform: capitalize;
}
</style>