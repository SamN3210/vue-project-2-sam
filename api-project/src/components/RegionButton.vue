<template>
    <router-link :to="regionPath" class="router-link">
        <button>{{region}}</button>
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
    background-color: #6279B8;
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