<template>
  <div id="wrapper">
    <Pokemon
      v-for="pokemon in allPokemon"
      :key="pokemon.id"
      :pokemon="pokemon"
    />
  </div>
</template>

<script>
import Pokemon from "./Pokemon.vue";
import useQuery from "../use/query";

export default {
  name: "Pokemons",
  components: {
    Pokemon
  },
  props: {},
  async setup() {
    const {
      pokemon: allPokemon = [],
    } = await useQuery(`{ pokemon { name imgSrc } }`);

    return { allPokemon };
  },
};
</script>

<style scoped>
  #wrapper {
    display: grid;
    grid-gap: 70px 20px;
    grid-template-columns: repeat(auto-fit, 200px);
    justify-content: space-evenly;
    margin: 80px auto 15vh;
    max-width: 1200px;
  }
</style>
