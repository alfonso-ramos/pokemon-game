<template>
  <PokemonPage />
</template>

<script>
import PokemonPage from './pages/pokemonPage.vue';

export default {
  name: 'App',
  components: {
    PokemonPage
  }
}


</script>

<style>
#app{
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
