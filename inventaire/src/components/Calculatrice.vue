<template>
  <b-container>
    <div class="calculatrice">
      <h1>Calculatrice</h1>
      <b-row>
        <b-col class="entries">
          <b-row class="nom_meuble my-2">
            <b-col>
              <b-form-input
                id="input-default"
                placeholder="Nom du meuble"
                v-model="nom_meuble"
              ></b-form-input>
            </b-col>
          </b-row>
          <!-- nom -->
          <b-row class="longueur_meuble my-2">
            <b-col>
              <b-form-input
                id="input-default"
                placeholder="Longueur du meuble (Cm)"
                v-model="longueur_meuble"
                type="number"
              ></b-form-input>
            </b-col>
          </b-row>
          <!-- longueur -->
          <b-row class="largeur_meuble my-2">
            <b-col>
              <b-form-input
                id="input-default"
                placeholder="Largeur du meuble (Cm)"
                v-model="largeur_meuble"
                type="number"
              ></b-form-input>
            </b-col>
          </b-row>
          <!-- largeur -->
          <b-row class="hauteur_meuble my-2">
            <!-- <b-col md="2">
            <label for="hauteur_meuble">Hauteur du meuble:</label>
          </b-col> -->
            <b-col>
              <b-form-input
                id="input-default"
                placeholder="Hauteur du meuble (Cm)"
                v-model="hauteur_meuble"
                type="number"
              ></b-form-input>
            </b-col>
          </b-row>
          <!-- hauteur -->
        </b-col>

        <b-col class="volume">
          <b-jumbotron class="my-1">
            <p>Le volume du meuble est de {{ volume_meuble }} m3</p>
          </b-jumbotron>
        </b-col>
      </b-row>
    </div>
  </b-container>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

export default {
  name: "CalculatriceItem",
  props: {},
  data: function() {
    return {
      nom_meuble: "",
      longueur_meuble: null,
      largeur_meuble: null,
      hauteur_meuble: null,
      aire: null,
      message: ""
    };
  },
  computed: {
    volume_meuble: function() {
      return (
        (this.longueur_meuble / 100 ) * (this.largeur_meuble  / 100 ) * (this.hauteur_meuble / 100 )
      );
    }
  },
  methods: {
    onlyNumber: function() {}
  }
};
</script>

<style scoped>
.calculatrice label {
  text-align: right;
}
</style>
