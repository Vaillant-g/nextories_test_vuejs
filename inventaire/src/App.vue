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
      liste: [
        {
          hauteur: "100",
          id: "Table4",
          largeur: "200",
          longueur: "200",
          nom: "Table"
        },
        {
          hauteur: "100",
          id: "Table23",
          largeur: "100",
          longueur: "300",
          nom: "Table2"
        },
        {
          hauteur: "100",
          id: "chaise1.5",
          largeur: "100",
          longueur: "150",
          nom: "chaise"
        }
      ]
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
