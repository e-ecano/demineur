<template>
  <div>

    <button @click="hideBomb">Voir les bombe :3</button>

    <!-- Grille -->
    <table class="grid">
      <tr class="cell"
          v-for="ligne in grille">
        <td class="cell"
            v-for="cellule in ligne" >
          <bomb :params="cellule"/>
        </td>
      </tr>
    </table>
    <!-- /Grille -->

    <!-- Grille Test-->
    <table class="grid">
      <tr class="cell"
          v-for="ligne in grille">
        <td class="cell"
            v-for="cellule in ligne">

          <bomb v-if="cellule.setBomb" :params="cellule"></bomb>

        </td>
      </tr>
    </table>
    <!-- /Grille Test-->

  </div>
</template>

<script>

  import Bomb from './bomb'

  export default {
    name: 'App',
    components: {Bomb},
    data () {

      const grille = []

      var nbAlea = 0
      var setBomb = false


      // Lignes
      for (var i = 0; i < 10; i++) {

        // Cellules
        var ligne = []
        for (var j = 0; j < 10; j++) {

          /*nbAlea = Math.random() * 100
          console.log(nbAlea)
          if (this.nbAlea < 20) {
            setBomb = true
          } else {
            setBomb = false
          }*/

          ligne.push({
            setBomb: Math.random() * 100 < 20
            //x: j,
            //y: i,
            //clique: false
          })

        }
        grille.push(ligne)

      }
      return {
        grille: grille
      }
    },
    methods: {
      hideBomb
    }
  }
</script>

<style>
  @import "stylesheets/style.scss";
</style>
