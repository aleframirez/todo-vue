<template>
  <div
    class="draggable-window"
    :style="{ top: posY + 'px', left: posX + 'px' }"
  >
    <div class="header" @mousedown="startDragging">
      <h3>Ventana flotante</h3>
    </div>
    <div class="content">
      <p>Aquí va el contenido de la ventana.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posX: 100, // Posición inicial en X
      posY: 100, // Posición inicial en Y
      dragging: false,
      offsetX: 0,
      offsetY: 0,
    };
  },
  methods: {
    startDragging(event) {
      this.dragging = true;
      // Calculamos el offset entre la posición del mouse y la posición de la ventana
      this.offsetX = event.clientX - this.posX;
      this.offsetY = event.clientY - this.posY;
      // Escuchamos el evento de movimiento del ratón
      document.addEventListener("mousemove", this.drag);
      document.addEventListener("mouseup", this.stopDragging);
    },
    drag(event) {
      if (this.dragging) {
        // Actualizamos la posición de la ventana
        this.posX = event.clientX - this.offsetX;
        this.posY = event.clientY - this.offsetY;
      }
    },
    stopDragging() {
      // Terminamos de arrastrar y removemos los eventos
      this.dragging = false;
      document.removeEventListener("mousemove", this.drag);
      document.removeEventListener("mouseup", this.stopDragging);
    },
  },
};
</script>

<style scoped>
.draggable-window {
  position: absolute;
  width: 300px;
  height: 200px;
  background-color: white;
  border: 1px solid #ccc;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  /* cursor: move; */
  z-index: 100;
}
.header {
  background-color: #f2f2f2;
  padding: 10px;
  cursor: move;
  border-bottom: 1px solid #ddd;
}
.content {
  padding: 20px;
}
</style>
