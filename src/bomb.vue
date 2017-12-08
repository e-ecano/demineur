<template>
  <div>
    <div @click="explode"
            @contextmenu.prevent="turnOff"
            class="bomb"
            :etat="true"
            ><span style="visibility: hidden">Q {{params.setBomb}}</span> <!-- Cacher le contenu de la div en la laissant cliquable -->
    </div>

  </div>
</template>

<script>
  export default {
    name: 'bomb',
    props:{
      params:{required: true, default: () => ({}), type: Object}
    },
    methods:{
      explode(){

        //var etat=true  // true=EXPLOSION ; false=pas de bombe

        if(this.params.setBomb){
          console.log("=== BOOM ! ===")
        }else{
          console.log("Il n'y a pas de bombe ici")
        }
      },
      turnOff(){

        //var etat=true

        if(this.params.setBomb){
          console.log("Bombe désactivée")
        }else{
          console.log("Il n'y a rien à désactiver ici")
        }
      },
      viewBomb(){
        if(this.params.showBomb){
          console.log("Jeu sans les réponses")
        }else{
          console.log("Jeu avec les réponses")
        }
      }
    }
  }
</script>
