<template>
    <div>
        <h1>Lista Combinadas de Tareas</h1>
        <div class="add-task-container">
        <div class="input-group">
            <input 
                v-model="newTask" 
                @keyup.enter="addTask" 
                placeholder="Añadir nueva tarea" 
                class="task-input"
            />
            <button @click="addTask" class="add-button">Añadir</button>
        </div>

        <div v-if="tasks.length > 0" class="task-list">
            <div v-for="task in tasks" :key="task.id" class="task-item">
                <span :class="{ completed: task.completed }">{{ task.todo }}</span>
                <div>
                    <button @click="toggleTaskCompletion(task)">
                        {{ task.completed ? 'Desmarcar' : 'Completar' }}
                    </button>
                    <button @click="deleteTask(task)">Eliminar</button>
                </div>
            </div>
        </div>
    </div><!-- Esta seccion es una combinación de las dos vistas anteriores -->
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: "CombinedView",
    data() {
        return {
            newtask: "", // Almacenamiento local de la nueva tarea
            tasks: [], // Almacenamiento local de las tareas traídas de la API
        };
    },
    created() {
        this.fetchTasks();
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
        },
        // Agregar una nueva tarea
        addTask() {
            if (this.newTask.trim() === "") return;

            const newTask = {
                todo: this.newTask,
                completed: false,
                id: Date.now(), 
            };

            // Añadir la nueva tarea al inicio de la lista
            this.tasks.unshift(newTask);
            this.newTask = ""; // Limpiar el campo de entrada después de agregar
        },

        // Elimina una tarea específica de la lista
        deleteTask(task) {
            this.tasks = this.tasks.filter((t) => t.id !== task.id);
        },

        // Cambia el estado de la tarea entre completada y no completada
        toggleTaskCompletion(task) {
            task.completed = !task.completed;
        },
   },
};
            // Aquí deberían realizar la solicitud a la API usando axios o fetch.
   // Esta sección debe permitir agregar tareas nuevas a la vez que extraer las tareas anteriores de la API
</script>

<style scoped>
.add-task-container {
    padding: 20px;
    max-width: 400px;
    margin: 0 auto;
}

.input-group {
    display: flex;
    margin-bottom: 10px;
}

.task-input {
    flex-grow: 1;
    padding: 8px;
    margin-right: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.add-button {
    padding: 8px 12px;
    border: none;
    border-radius: 4px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
}

.task-list {
    margin-top: 20px;
}

.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #eee;
}

.completed {
    text-decoration: line-through;
    color: gray;
}
</style>
/* Aquí pueden agregar estilos personalizados para el componente. 