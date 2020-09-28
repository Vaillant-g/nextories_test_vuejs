<template>
  <div id="app">
    <Calculatrice :liste="this.liste" />
    <Inventaire :liste="this.liste" />
  </div>
</template>

<script>
import Calculatrice from "./components/Calculatrice.vue";
import Inventaire from "./components/Inventaire.vue";
import Vue from "vue";
import { BootstrapVue, IconsPlugin } from "bootstrap-vue";

Vue.use(BootstrapVue);
Vue.use(IconsPlugin);

export default {
  name: "App",
  components: {
    Calculatrice,
    Inventaire
  },
  data: function() {
    return {
      liste: []
    };
  }
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
h1 {
  text-align: left;
}

ul {
  list-style: none;
}
</style>
