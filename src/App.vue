<template>
  <div>
    <table class="grid">
      <tr class="cell"
          v-for="ligne in grille">
        <td class="cell"
            v-for="cellule in ligne"
            :class="cellule.clique ? 'red' : 'green'"
            @click="click(cellule)">{{cellule.bombe}}<bomb/></td>
      </tr>
    </table>
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
      for(var i = 0; i<10; i++){
        // Cellules
        var ligne = []
        for(var j = 0; j<10; j++){
          ligne.push({
            bombe: true,
            x: j,
            y: i,
            clique: false
          })
        }
        grille.push(ligne)

      }
      return {
        grille: grille
      }
    },
    methods: {
      click(cellule){
        console.log(`x: ${cellule.x} - y:${cellule.y}`)
        cellule.clique = true
        //if (bomb.etat === false){
          //console.log(`=== Il n'y a pas de bombe en `)
        //}
      },
    }
  }
</script>

<style>
  @import "stylesheets/style.scss";
</style>
