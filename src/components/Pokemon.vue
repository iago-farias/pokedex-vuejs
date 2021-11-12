<template>
  <div class="mt-4">
    <div class="card">
      <div class="card-image">
        <figure>
          <img
            :src="currentImage"
            alt="Placeholder image"
          />
        </figure>
      </div>
      <div class="card-content">
        <div class="media">
          <div class="media-content">
            <p class="title is-4">{{number}} - {{name | nameFormat}}</p>
            <p class="subtitle is-6">Tipo: {{pokemon.type}}</p>
          </div>
        </div>
        <div class="content">
          <button class="button is-info" @click="handleChangeSprite">Mudar sprite</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  created: async function() {
    const response = await axios.get(this.url);

    this.pokemon.type = response.data.types[0].type.name;
    this.pokemon.spriteFront = response.data.sprites.front_default;
    this.pokemon.spriteBack = response.data.sprites.back_default;
    this.currentImage = this.pokemon.spriteFront;
  },
  data() {
    return {
      isFront: true,
      currentImage: '',
      pokemon: {
        type: '',
        spriteFront: '',
        spriteBack: '',
      }
    }
  },
  props: {
    number: Number,
    name: String,
    url: String,
  },
  filters: {
    nameFormat(value) {
      const nameFormated = value[0].toUpperCase() + value.slice(1);

      return nameFormated;
    },
  },
  methods:{
    handleChangeSprite(){
      if(this.isFront){
        this.isFront = false;
        this.currentImage = this.pokemon.spriteBack;

        return;
      }

      this.isFront = true;
      this.currentImage = this.pokemon.spriteFront;
    }
  }
};
</script>

<style>
</style>