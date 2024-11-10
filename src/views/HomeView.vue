<template>
  <div class="home">
    <img class="rounded-logo" alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Bienvenidos a la aplicación de gestor de tareas hecha con Vue.js"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>
<style scoped>
.rounded-logo {
  border-radius: 50%; /* Esto hará que la imagen sea circular */
  width: 100px; /* Ajusta el tamaño según sea necesario */
  height: 100px; /* Ajusta el tamaño según sea necesario */
  object-fit: cover; /* Esto asegura que la imagen mantenga su aspecto al recortarse */
}
</style>
