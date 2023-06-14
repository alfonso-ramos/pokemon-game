<template>
    <div>
        <h1>¿Quién es este pokémon?</h1>
    </div>
    <div>
        <PokemonImage :pokemonId="5" :showPokemon="true"/>
        <PokemonOptions />
    </div>
</template>

<script setup>
import PokemonImage from '@/components/PokemonImage.vue';
import PokemonOptions from '@/components/PokemonOptions.vue';


</script>
