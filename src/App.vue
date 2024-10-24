<template>
  <div id="app" class="container">
    <h1 class="m-3 p-3 text-center">
      Tablero de Mensajes
    </h1>
    <div class="row container" v-if="usuarios.length" id="vistaChat">
      <div class="col-3">
        <CardUsuario
          :imagenUsuario="usuarios[0].picture.large"
          :nombreUsuario="usuarios[0].name.first"
          alineacion="left"
          @enviarMsg="agregarChat"
          @keypress.enter="agregarChat"
        />
      </div>
      <div class="col-6">
        <CardChat :mensajes="mensajes" />
      </div>
      <div class="col-3">
        <CardUsuario
          :imagenUsuario="usuarios[1].picture.large"
          :nombreUsuario="usuarios[1].name.first"
          alineacion="right"
          @enviarMsg="agregarChat"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import CardChat from "./components/CardChat.vue";
import CardUsuario from "./components/CardUsuario.vue";

export default {
  name: "App",
  components: {
    CardChat,
    CardUsuario,
  },
  data() {
    return {
      usuarios: [],
      mensajes: [],
    };
  },
  methods: {
    agregarChat: function (nuevoMsg) {
      this.mensajes.push(nuevoMsg);
      console.log(this.mensajes);
    },
  },
  async mounted() {
    try {
      let response = await axios.get("https://randomuser.me/api/?results=2");
      let { data } = response;
      this.usuarios = data.results;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>

<style>

</style>