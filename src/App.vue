<template>
  <div>

    <h1>Démineur</h1>
    <h2>Grille 1</h2>
    <p>Les bombes répondent aux clique<br/>
      À faire :<br>
      - changer le background-color au click<br/>
      - indiquer les bombes "actives" autour de la div cliquée
    </p>
    <!-- Grille, toutes les bombes répondent au clique -->
    <table class="grid">
      <tr class="cell"
          v-for="ligne in grille">
        <td class="cell"
            v-for="cellule in ligne"
            @click="click(cellule)">
          <div >
            <bomb :params="cellule"/>
          </div>

        </td>
      </tr>
    </table>
    <!-- /Grille -->

    <h2>Grille 2</h2>
    <p>
      Les bombes "inactivent" ne répondent pas aux cliques
    </p>
    <!-- Grille Test, les bombes "inactives" ne répondent pas au clique-->
    <table class="grid">
      <tr class="cell"
          v-for="ligne in grille">
        <td class="cell"
            v-for="cellule in ligne"
            @click="click(cellule)">{{cellule.bombe}}

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

      // Lignes
      for (var i = 0; i < 10; i++) {
        // Cellules
        var ligne = []
        for (var j = 0; j < 10; j++) {
          ligne.push({
            setBomb: Math.random() * 100 < 20,
            x: j,
            y: i,
          })
        }
        grille.push(ligne)
      }
      return {
        grille: grille,
      }
    },
    methods: {
      click(cellule){
        console.log(`x: ${cellule.x} - y:${cellule.y}`)
      }
    }
  }
</script>

<style>
  @import "stylesheets/style.scss";
</style>
