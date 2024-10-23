<template>
  <div class="p-3">
    <h1 class="text-center">Centro de Mensajes</h1>

    <div class="row container">

      <div class="col-3 carta">
        <CardUser/>
      </div>

      <div class="col-6 carta">
        <h1>CardChat.vue</h1>
      </div>

      <div class="col-3 carta">
        <h1>CardUsuario.vue</h1>
      </div>

    </div>
  </div>
</template>


<script>
import axios from "axios";
import CardUser from "./components/CardUser.vue"
import CardChat from "./components/CardChat.vue"

export default {
  name: "App",
  components: {
    CardChat,
    CardUser,
  },
  data (){
    return{
      usuario:[],
      mensaje:[],
    };
  },
  methods:{
    agregarChat(nuevoMsj){
      this.mensajes.push(nuevoMsj);
    }
  },
  async mounted(){
    const response = await axios.get("https://randomuser.me/api/?results=2")
    this.usuario = response.data.results;
  }
}
</script>



<style scoped>
.carta {
  border: black 1px solid;
}

</style>
