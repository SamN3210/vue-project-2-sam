<template>
    <h3 :style="backgroundColor">{{type}}</h3>
</template>

<script>
    export default {
        name:"PokemonTypes",
        props: {
            type:String
        },
        data(){
            return{
                colors: {
                grass: "#d5faa3",
                fire: "#ffa83e",
                water: "#0077b6",
                electric: "#ffd000",
                bug: "#c9d019",
                dark: "#343a40",
                fairy: "#faa5e4",
                poison: "#a755c2",
                fighting: "#a35200",
                ice: "#caf0f8",
                psychic: "#ff4d80",
                ghost: "#8b728e",
                flying: "#c2dfe3",
                steel: "#7c90a0",
                ground: "#7f4f24",
                rock: "#d4a276",
                dragon: "#6730ec",
                normal: "#e9ecef",
            }
            }
        },
        computed:{
            backgroundColor:function(){
                return "background-color: " + this.colors[`${this.type}`];
            }
        }
    }
</script>

<style>

</style>