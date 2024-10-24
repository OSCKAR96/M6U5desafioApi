<template>
    <div ref="chatContainer" class="border">
      <div v-for="(mensaje, index) in mensajes" :key="index" :style="{ textAlign: mensaje.alineacion }">
        <div>
          <span><small>{{ mensaje.autor }}</small></span>
          <div>
            <span :style="{ backgroundColor: mensaje.color, textAlign: mensaje.alineacion }">
              {{ mensaje.texto }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "CardChat",
    props: {
      mensajes: Array,
    },
  };
  </script>
  
  <style scoped>
  
  </style>