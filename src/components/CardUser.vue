<template>
<div>
  <div>
    <div>
      <img src="../../src/assets/logo.svg" alt="imagenUsuario" class="">
    </div>
    <div>
      <span></span>
    </div>
  </div>
</div>
</template>


<script>
export default {
  name: "CardUser",
  props: {
    imagenUsuario: String,
    nombreUsuario: String,
    posicion: String,
  },
  data(){
    return{
      colorChat:"",
      textoChat:"",
    }
  },
  methods:{
    enviarMsj: function(){
      let mensajeChat = {
        autor: this.nombreUsuario,
        color: this.colorChat,
        texto: this.textoChat,
        posicion: this.posicion,
      }
      
    }
  }
}

</script>


<style scoped>

</style>
