<template>
  <ul class="list-group">
    <vue-filter />
    <vue-footer v-if="todos.length !== 0" />
    <vue-items v-for="todo in todos" :key="todo.id" :todo="todo" />
    <li v-if="todos.length === 0" class="list-group-item">
      No hay tareas
    </li>
  </ul>
</template>

<script>
import { provide, computed, inject, ref } from "vue";
import VueItems from "./VueItems.vue";
import VueFooter from "./VueFooter.vue";
import VueFilter from "./VueFilter.vue";
export default {
  components: { VueItems, VueFooter, VueFilter },
  setup() {
    const todosTodo = inject("todos");

    const estado = ref("all");

    const todos = computed(() => {
      if (estado.value === "all") {
        return todosTodo.value;
      }
      if (estado.value === "actives") {
        return todosTodo.value.filter((item) => item.estado === false);
      }
      if (estado.value === "complete") {
        return todosTodo.value.filter((item) => item.estado === true);
      }
    });
    provide("estado", estado);
    return { todos };
  },
};
</script>

<style></style>
