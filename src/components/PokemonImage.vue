<template>
    <div class="pokemon-container">
        <img :src="ImgSrc" alt="pokemon" class="pokemon-hidden">
        <img v-if="showPokemon" :src="ImgSrc" alt="pokemon" class="fade-in">
    </div>
</template>

<script>
export default{

    props:{
        pokemonId: {
            type: Number,
            required: true
        },
        showPokemon: {
            type: Boolean,
            required: true,
            default: false
        } 
    },

    computed:{
        ImgSrc() {
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
        }
    }
    
}

</script>

<style scoped>
.pokemon-container {
    height: 200px;
}
img {
    height: 200px;
    position: absolute;
    right: 32%;
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}
.pokemon-hidden{
    filter: brightness(0);
}
</style>