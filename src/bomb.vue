<template>
  <div>
    <button @click="explode"
            @contextmenu.prevent="turnOff"
            class="bomb"
            :etat="true"
            >Q
    </button>

  </div>
</template>

<script>
  export default {
    name: 'bomb',
    props: {
      bomb: {
        required: false,
        default: () => ({
          etat: true
        })
      }
    },
    methods:{
      explode(){
        console.log("=== EXPLOSION ! ===")
      }
    }
  }
</script>
