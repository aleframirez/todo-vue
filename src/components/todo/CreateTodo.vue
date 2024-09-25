<template>
  <section class="create-todo">
    <h3>CREATE A TODO</h3>

    <form id="new-todo-form" @submit.prevent="addTodo">
      <h4>What's on your todo list?</h4>
      <input
        type="text"
        name="content"
        id="content"
        placeholder="e.g. make a video"
        v-model="input_content"
      />

      <h4>Pick a category</h4>
      <div class="options">
        <label>
          <input
            type="radio"
            name="category"
            id="category1"
            value="business"
            v-model="input_category"
          />
          <span class="bubble business"></span>
          <div>Business</div>
        </label>

        <label>
          <input
            type="radio"
            name="category"
            id="category2"
            value="personal"
            v-model="input_category"
          />
          <span class="bubble personal"></span>
          <div>Personal</div>
        </label>
      </div>

      <input type="submit" value="Add todo" />
    </form>
  </section>
</template>

<script setup>
import { ref, watch } from "vue";

const input_content = ref("");
const input_category = ref(null);

const emit = defineEmits(["add-todo"]);

const addTodo = () => {
  if (input_content.value.trim() === "" || !input_category.value) return;

  // Emitimos un evento con la nueva tarea
  const newTodo = {
    content: input_content.value,
    category: input_category.value,
    done: false,
    editable: false,
    createdAt: new Date().getTime(),
  };
  // console.log(newTodo);

  // Emitir evento a componente padre
  emit("add-todo", newTodo);

  // Reseteamos los inputs
  input_content.value = "";
  input_category.value = null;
};
</script>
