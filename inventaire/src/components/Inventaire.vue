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
            <b-row>
              <b-col md="1">
                <b-form-checkbox
                  :id="item.id"
                  v-on:change="toggle_checkbox(item.id)"
                ></b-form-checkbox>
              </b-col>
              <b-col md="10">
                <h4>
                  {{ item.nom }}
                  <span class="float_right">
                    <b-icon
                      icon="trash"
                      v-on:click="
                        liste.splice(
                          liste.findIndex(x => x.id === item.id),
                          1
                        )
                      "
                    ></b-icon
                  ></span>
                </h4>
                <p>{{ volume(item) + "m3" }}</p>
              </b-col>
            </b-row>
          </li>
        </ul>
      </div>
      <b-button
        v-show="this.listes_meubles_selectionnes.length !== 0"
        class="float_left"
        v-on:click="suppression_meubles_selectionnes"
        variant="danger"
        >Supprimer les meubles sélectionnés</b-button
      >
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
      liste_meubles: [],
      listes_meubles_selectionnes: []
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
    },
    toggle_checkbox: function(e) {
      let index = this.listes_meubles_selectionnes.indexOf(e);
      if (index === -1) {
        this.listes_meubles_selectionnes.push(e);
      } else this.listes_meubles_selectionnes.splice(index, 1);
      //      console.log(this.listes_meubles_selectionnes);
    },
    suppression_meubles_selectionnes: function() {
      this.listes_meubles_selectionnes.forEach(element => {
        this.liste.splice(
          this.liste.findIndex(
            x => x.id === element
          ),
          1
        );
      });
      this.listes_meubles_selectionnes = [];
    }
  }
};
</script>

<style scoped>
.Inventaire {
  margin-top: 50px;
}
li {
  text-align: left;
}

.liste_meubles {
  box-shadow: 0 0.125rem 0.25rem rgba(0, 0, 0, 0.075) !important;
}

.float_right {
  float: right;
}

.float_left {
  float: left;
}
</style>
