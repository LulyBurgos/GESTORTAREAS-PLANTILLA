<template>
    <div class="task-list">
        <h1>Lista de Tareas</h1>
        <!-- Formulario para agregar una nueva tarea -->
        <button @click="fetchTasks">Cargar Tareas</button>
        <div v-if="tasks.length > 0">
            <div v-for="task in tasks" :key="task.id">
                <TodoItem :title="task.todo" :completed="task.completed" @toggle-completion="toggleTaskCompletion(task)" @delTodo= "deleteTask(task)" />          
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import TodoItem from '../components/TodoItem.vue';
export default {
    name: "TaskList",
    components: {TodoItem},
    data() {
        return {
            tasks: [], // Almacenamiento local de las tareas traídas de la API
        };
    },
    methods: {
        // Llamada para obtener las tareas desde la API externa
        fetchTasks() {
            axios // Usamos axios para realizar la solicitud
                .get('https://dummyjson.com/todos') // URL de la API
                .then((response) => {
                    this.tasks = response.data.todos; // Almacenamos las tareas en el estado local
                })
                .catch((error) => {
                    console.log(error);
                });
            // Aquí deberían realizar la solicitud a la API usando axios o fetch.
            // La URL que usaremos es: https://dummyjson.com/todos

            // Sugerencia: Intentar implementarlo con axios o fetch
        },

        // Cambiar el estado de una tarea (completada/no completada)
        toggleTaskCompletion(task) {
            task.completed = !task.completed;
        },

        // Eliminar la tarea seleccionada
        deleteTask(task) {
            this.tasks = this.tasks.filter((t) => t.id !== task.id);
        },
    },
};
</script>

<style scoped>
/* Aquí pueden experimentar con estilos de tu preferencia */
</style>