<template>
  <div id="app">
    <div class="columns">
      <div class="column is-half is-offset-one-quarter">
        <img src="./assets/pokeapi.png" alt="pokeapi logo" />
        <hr>
        <div v-for="(pokemon, index) in pokemons" :key="index">
          <Pokemon
            :name="pokemon.name"
            :url="pokemon.url"
            :number="index + 1"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Pokemon from "./components/Pokemon.vue";

import pokeapi from "./service/pokeapi";

export default {
  name: "App",
  data() {
    return {
      pokemons: [],
    };
  },
  components: {
    Pokemon,
  },
  created: async function () {
    const response = await pokeapi.get("/pokemon?limit=150&offset=0");
    this.pokemons = response.data.results;
  },
};
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  padding: 18px;
}
</style>
