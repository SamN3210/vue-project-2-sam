<template>
    <router-link :to="regionPath" class="router-link">
        <button @click="$emit('link')">{{region}}</button>
    </router-link>
</template>

<script>
export default {
    props: {
        region: String,
    },
    computed: {
        regionPath: function() {
            return `/pokemons/${this.region.toLowerCase()}`
        }
    }
}
</script>

<style scoped>
.router-link,
.router-link:visited,
.router-link:link {
    width: 100%;
    border-radius: 10px;
    margin: 1rem;
}
button{
    width: 5vw;
    margin: 1rem;
    background-color: var(--main-black);
    color:white;
    height: 5vh;
    border-radius: 10px;
}
h1{
    text-transform: capitalize;
}
</style>