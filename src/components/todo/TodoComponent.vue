<template>
  <main class="app">
    <section class="greeting">
      <h2 class="title">
        What's up,
        <input type="text" id="name" placeholder="Name here" v-model="name" />
      </h2>
    </section>

    <CreateTodo @add-todo="addTodo" />

    <TodoList :todos="todos_asc" @remove-todo="removeTodo" />
  </main>
</template>

<script setup>
import { ref, onMounted, computed, watch } from "vue";
import CreateTodo from "./CreateTodo.vue";
import TodoList from "./TodoList.vue";

const todos = ref([]);
const name = ref("");

// Ordenamos los todos de mas nuevos a mas antiguos
const todos_asc = computed(() =>
  todos.value.sort((a, b) => {
    return b.createdAt - a.createdAt;
  })
);

// Función para agregar una nueva tarea
const addTodo = (todo) => {
  todos.value.push(todo);
};

// Funcion para eliminar tarea
const removeTodo = (todo) => {
  todos.value = todos.value.filter((t) => t !== todo);
};

// Guardamos los datos en el localStorage
watch(
  todos,
  (newVal) => {
    localStorage.setItem("todos", JSON.stringify(newVal));
  },
  {
    deep: true,
  }
);

watch(name, (newVal) => {
  localStorage.setItem("name", newVal);
});

onMounted(() => {
  name.value = localStorage.getItem("name") || "";
  todos.value = JSON.parse(localStorage.getItem("todos")) || [];
});
</script>
