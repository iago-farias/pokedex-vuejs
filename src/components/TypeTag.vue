<template>
  <span class="tag is-rounded" v-bind:style="backgroundColor">{{ type }}</span>
</template>

<script>
export default {
  created: function () {
    switch (this.type) {
      case "grass":
        this.backgroundColor = this.backgroundColor + "#79C63C;";
        break;
      case "fire":
        this.backgroundColor = this.backgroundColor + "#EF4311;";
        break;
      case "electric":
        this.backgroundColor = this.backgroundColor + "#E69303;";
        break;
      case "water":
        this.backgroundColor = this.backgroundColor + "#116DCA;";
        break;
      case "bug":
        this.backgroundColor = this.backgroundColor + "#89980E;";
        break;
      case "normal":
        this.backgroundColor = this.backgroundColor + "#C2BDB4;";
        break;
      case "rock":
        this.backgroundColor = this.backgroundColor + "#9E863D;";
        break;
      case "dark":
        this.backgroundColor = this.backgroundColor + "#3D2D22;";
        break;
      case "fairy":
        this.backgroundColor = this.backgroundColor + "#E190E1;";
        break;
      case "flying":
        this.backgroundColor = this.backgroundColor + "#6072D5;";
        break;
      case "ground":
        this.backgroundColor = this.backgroundColor + "#B79A48;";
        break;
      case "poison":
        this.backgroundColor = this.backgroundColor + "#944796;";
        break;
      case "steel":
        this.backgroundColor = this.backgroundColor + "#B8B8C5;";
        break;
      case "psychic":
        this.backgroundColor = this.backgroundColor + "#EE457F;";
        break;
      case "ice":
        this.backgroundColor = this.backgroundColor + "#71D5F6;";
        break;
      case "ghost":
        this.backgroundColor = this.backgroundColor + "#5D5DAF;";
        break;
      case "fighting":
        this.backgroundColor = this.backgroundColor + "#7F331C;";
        break;
      case "dragon":
        this.backgroundColor = this.backgroundColor + "#745CDD;";
        break;
      default:
        return;
    }
  },
  data() {
    return {
      backgroundColor: "background-color: ",
    };
  },
  props: {
    type: String,
  },
};
</script>

<style scoped>
  .tag {
    text-transform: uppercase;
    letter-spacing: 0.2rem;
    font-weight: bold;
    color: #fff;
  }
</style>