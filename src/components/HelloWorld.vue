<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Para mas proyectos puedes visitar el repositorio de mi proyectos en
      <a href="https://github.com/LulyBurgos?tab=repositories" target="_blank" rel="noopener">Mi GITHUB</a>.
    </p>
    <h3>Funcionalidad de la aplicación</h3>
    <ul>
      <li><p>Añadir Tareas</p></li>
      <li><p>Lista de tareas</p></li>
      <li><p> Tareas combinadas</p></li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
