<template>
  <div class="border">
    <div class="d-block">
      <div class="p-2 text-center">
        <img :src="imagenUsuario" :alt="nombreUsuario" />
      </div>
      <div class="p-2 text-center">
        <span>{{ nombreUsuario }}</span>
      </div>
      <form @submit.prevent="enviarMsg">
        <div class="p-2">
          <label for="colorTexto"><small>Color del chat:</small></label>
          <input id="colorTexto" type="color" v-model="colorChat" />
        </div>
        <div class="p-2">
          <label for="textoMensaje"><small>Mensaje:</small></label>
          <textarea rows="3" v-model="textoChat" @keyup.enter="enviarMsg"></textarea>
          <label for="enviarMsg"><small>Click o pulsa ENTER para enviar el mensaje...</small></label>
        </div>
        <div class="p-2 text-end">
          <button>Enviar</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardUsuario",
  props: {
    imagenUsuario: String,
    nombreUsuario: String,
    alineacion: String,
  },
  data() {
    return {
      colorChat: "#fff000",
      textoChat: "",
    };
  },
  methods: {
    enviarMsg: function () {
      let mensajeChat = {
        autor: this.nombreUsuario,
        color: this.colorChat,
        texto: this.textoChat,
        alineacion: this.alineacion,
      };
      if (this.textoChat.length > 0 && this.textoChat != "\n") {
        this.$emit("enviarMsg", mensajeChat);
      }
      this.textoChat = "";
    },
  },
};
</script>

<style scoped>

</style>