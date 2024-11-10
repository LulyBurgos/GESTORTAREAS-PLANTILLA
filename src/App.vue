<template>
  <div id="app">
    <!-- Barra de navegación con enlaces a diferentes rutas -->
    <nav>
      <div class="navbar-brand">
        <span class="vue-icon">
          <!-- Logo de Vue en SVG -->
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 261.76 226.69" width="24" height="24">
            <path fill="#42b883" d="M130.88,0l-130.88,0l130.88,226.69l130.88-226.69h-52.352l-78.528,135.658l-78.528-135.658h-52.352l130.88,226.69l130.88-226.69h-52.352z"/>
            <path fill="#35495e" d="M0,0h52.352l78.528,135.658l78.528-135.658h52.352l-130.88,226.69l-130.88-226.69z"/>
          </svg>
        </span>
        <router-link to="/" class="nav-link">Gestor de Tareas</router-link>
      </div>
      <router-link to="/addtask">Agregar Tarea</router-link> ||
      <router-link to="/tasklist">Lista de Tareas</router-link> ||
      <router-link to="/combined">Tareas Combinadas</router-link>
    </nav>
    <!-- Aquí se cargará el componente correspondiente a la ruta seleccionada -->
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
nav {
  background-color: #007bff;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.navbar-brand {
  display: flex;
  align-items: center;
  margin-right: 20px;
  text-decoration: none;
}

.vue-icon {
  margin-right: 10px;
}

.nav-link {
  color: #f8f9fa;
  font-weight: bold;
  text-decoration: none;
  margin: 0 20px;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>