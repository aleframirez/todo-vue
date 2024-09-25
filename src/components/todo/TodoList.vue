<template>
  <section class="todo-list">
    <h3>TODO LIST</h3>
    <div class="list" id="todo-list">
      <div
        v-for="todo in todos"
        :key="todo.createdAt"
        :class="`todo-item ${todo.done && 'done'}`"
      >
        <label>
          <input type="checkbox" v-model="todo.done" />
          <span :class="`bubble ${todo.category}`"></span>
        </label>

        <div class="todo-content">
          <input type="text" v-model="todo.content" />
        </div>

        <div class="actions">
          <button class="delete" @click="remove(todo)">Delete</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// import { defineProps, defineEmits } from "vue";

const props = defineProps({
  todos: Array, // Recibimos las tareas desde el componente padre
});

const emit = defineEmits(["remove-todo"]); // Emitimos evento para eliminar

const remove = (todo) => {
  emit("remove-todo", todo); // Emitimos evento al componente padre
};
</script>
