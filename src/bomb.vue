<template>
  <div>
    <button @click="explode"
            @contextmenu.prevent="turnOff"
            class="bomb"
            :etat="true"
            >Q {{params.setBomb}}
    </button>

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
      }
    }
  }
</script>
