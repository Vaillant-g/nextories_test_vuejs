<template>
  <b-container>
    <div class="Inventaire">
      <b-row>
        <b-col><h1>Inventaire</h1> </b-col>
        <b-col
          ><h1>Volume total : {{ volume_total }} m3</h1>
        </b-col>
      </b-row>
      <div class="liste_meubles">
        <ul id="example-1">
          <li v-for="item in liste" :key="item.id">
            <h4>{{ item.nom }}</h4>
            <p>{{ volume(item) + "m3" }}</p>
          </li>
        </ul>
      </div>
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
    volume_total: function() {
      var volume_total = 0;
      for (let i = 0; i < this.liste.length; i++) {
        volume_total += this.volume(this.liste[i]);
      }
      return Math.round(volume_total * 100) / 100;
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

.liste_meubles {
  box-shadow: 0 0.125rem 0.25rem rgba(0, 0, 0, 0.075) !important;
}
</style>
