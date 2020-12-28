<template>
  <div
    role="alert"
    :class="['alert', !todo.estado ? 'alert-danger' : 'alert-success tachado']"
  >
    <div class="d-flex bd-highlight ">
      <div class="bd-highlight flex-grow-1">
        <h4 style=" text-transform: capitalize;">
          {{ todo.texto }}
        </h4>
      </div>

      <span class="bd-highlight px-4">{{ todo.fechaCreado }}</span>

      <div class="bd-highlight">
        <button type="button" class="btn btn-success" @click="cambiar(todo.id)">
          Completada
        </button>
        <button type="button" class="btn btn-danger" @click="eliminar(todo.id)">
          Eliminar
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import { inject } from "vue";
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  setup() {
    const todos = inject("todos");

    const eliminar = (id) => {
      todos.value = todos.value.filter((item) => item.id !== id);
    };

    const cambiar = (id) => {
      todos.value = todos.value.map((item) => {
        if (item.id === id) {
          item.estado = true;
        }
        return item;
      });
    };

    return { eliminar, cambiar };
  },
};
</script>
<style>
.tachado {
  text-decoration: line-through;
}
</style>
