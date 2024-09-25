<template>
  <div>
    <TodoComponent />
    <!-- <VentanaFlotante /> -->
  </div>
</template>

<script setup>
// import VentanaFlotante from "./components/VentanaFlotante.vue";
import TodoComponent from "./components/todo/TodoComponent.vue";
</script>

<!-- <style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: cursive;
}

input:not([type="radio"]):not([type="checkbox"]),
button {
  appearance: none;
  border: none;
  outline: none;
  background: none;
  cursor: initial;
}

body {
  background: var(--light);
  color: var(--dark);
}

section {
  margin-top: 2rem;
  margin-bottom: 2rem;
  padding-left: 1.5rem;
  padding-right: 1.5em;
}

h3 {
  color: var(--dark);
  font-size: 1rem;
  font-weight: 400;
  margin-bottom: 0.5rem;
}

h4 {
  color: var(--grey);
  font-size: 0.875rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}
</style> -->
