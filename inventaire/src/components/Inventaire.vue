<template>
  <b-container>
    <div class="Inventaire">
      <h1>Inventaire</h1>
      <ul id="example-1">
        <li v-for="item in liste" :key="item.nom">
          <h4>{{ item.nom }} </h4>
          <p> {{ volume(item) + "m3" }} </p>
        </li>
      </ul>
    </div>
  </b-container>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

export default {
  name: "InventaireItem",
  props: { liste: Array },
  data: function() {
    return {
      liste_meubles: []
    };
  },
  computed: {
    volume_meuble: function() {
      var volume =
        (this.longueur_meuble / 100) *
        (this.largeur_meuble / 100) *
        (this.hauteur_meuble / 100);
      return Math.round(volume * 100) / 100;
    }
  },
  methods: {
    volume: function(meuble) {
      let volume =
        (meuble.longueur / 100) *
        (meuble.largeur / 100) *
        (meuble.hauteur / 100);
      return Math.round(volume * 100) / 100;
    }
  }
};
</script>

<style scoped>
li {
  text-align: left;
}
</style>
