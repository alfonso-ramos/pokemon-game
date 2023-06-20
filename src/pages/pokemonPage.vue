<template>
    <div v-if="!pokemon">
        <h1>Espere porfavor</h1>
    </div>
    <div v-else="pokemon">
        <h1>¿Quién es este pokémon?</h1>
        <PokemonImage :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
        <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer"/>

        <h2> {{ message }}</h2>

        <button v-if="showPokemon" @click="newGame">
            Nuevo juego
        </button>
    </div>
</template>

<script>
import PokemonImage from '@/components/PokemonImage.vue';
import PokemonOptions from '@/components/PokemonOptions.vue';

import getPokemonOption from "@/helpers/getPokemonOptions";

export default {
    components: {
        PokemonImage, PokemonOptions
    },
    data() {
        return {
            pokemonArr: [],
            pokemon: null,
            showPokemon: false,
            message: ''
        }
    },
    methods: {
        async mixPokemonArr() {
            this.pokemonArr = await getPokemonOption()
            //Random Int
            const rndInt = Math.floor(Math.random() * 4)
            this.pokemon = this.pokemonArr[rndInt]
        },
        checkAnswer(pokemonID) {
            if (pokemonID === this.pokemon.id){
                this.showPokemon = true
                this.message = 'You Catch it.'
            } else {
                this.message = 'Try again.'
            }
        },
        newGame(){
            this.mixPokemonArr(),
            this.showPokemon = false
            this.message = '',
            this.pokemonArr = [],
            this.pokemon = null
        }
    },
    mounted() {
        this.mixPokemonArr()
    }
}

</script>
