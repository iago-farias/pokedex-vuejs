<template>
  <div id="app">
    <div class="columns">
      <div class="column is-half is-offset-one-quarter">
        <img src="./assets/pokeapi.png" alt="pokeapi logo" />
        <hr>
        <input 
          class="input is-rounded" 
          type="text" 
          placeholder="Buscar pokémon pelo nome"
          v-model="search"
        >
        <button class="button is-success mt-4" @click="handleSearch">Buscar</button>

        <div v-for="(pokemon, index) in filteredPokemons" :key="pokemon.url">
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
      filteredPokemons: [],
      search: ''
    };
  },
  components: {
    Pokemon,
  },
  methods: {
    handleSearch(){
      this.filteredPokemons = this.pokemons

      if(this.search.trim() === ''){
        this.search = '';
        return;
      }

      this.filteredPokemons = this.pokemons.filter(pokemon => pokemon.name.toUpperCase() == this.search.toUpperCase());
    }
  },
  created: async function () {
    const response = await pokeapi.get("/pokemon?limit=150&offset=0");
    this.pokemons = response.data.results;
    this.filteredPokemons = response.data.results;
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
