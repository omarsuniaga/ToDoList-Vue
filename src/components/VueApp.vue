<template>
  <div>
    <h2>Lista de Tareas</h2>
    <vue-form />
    <vue-list />
  </div>
</template>
<script>
import { provide, ref, watchEffect } from "vue";
import VueForm from "./VueForm.vue";
import VueList from "./VueList.vue";
export default {
  components: { VueForm, VueList },
  setup() {
    const todos = ref([]);
    provide("todos", todos);

    if (localStorage.getItem("todos")) {
      todos.value = JSON.parse(localStorage.getItem("todos"));
    }
    watchEffect(() => {
      //permite monitorear los cambio de algun estado
      //console.log(todos.value.length);
      //console.log(todos.value);
      localStorage.setItem("todos", JSON.stringify(todos.value));
    });
  },
};
</script>
