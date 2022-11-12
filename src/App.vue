<template>
  <div>
    <h1>{{ pokeName }}</h1>
    <img :src="pokeImg" />

    <h1>Daniel Burbano</h1>
    <h1>Alex Yamba</h1>
    <h2>11/11/2022</h2>
    <h3>Automatización de los procesos de software</h3>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  components: {
    
  },
  data() {
    return {
      pokeImg: null,
      pokeName: null,
    };
  },
  methods: {
    async showPoke() {
      const random = (Math.floor(Math.random() * 648)) + 1;
      const url = `https://pokeapi.co/api/v2/pokemon/${random}/`;
      const data = await (await axios.get(url)).data;
      this.pokeImg = data.sprites.other.dream_world.front_default;
      this.pokeName = data.name;
    },
  },
  mounted() {
    this.showPoke();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin: auto;
}
</style>
