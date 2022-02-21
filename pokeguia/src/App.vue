<template>
  <img alt="Vue logo" src="./assets/pokemon.png">
  <Pokeapp/>
</template>

<script>
import Pokeapp from "./components/Pokeapp.vue";
export default {
  name: "App",
  components: {
    Pokeapp,
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
}
</style>
