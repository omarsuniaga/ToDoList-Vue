<template>
  <div class="container">
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <span class="navbar-brand">Practicas usando Vue3/Boostrap5</span>

        <form class="d-flex input-group w-auto" @submit.prevent="formulario">
          <input
            type="text"
            class="form-control"
            placeholder="Escribe tu lista de tareas"
            aria-label="Agregar"
            v-model.trim="texto"
            autofocus
          />
          <button
            class="btn btn-outline-success"
            type="button"
            data-mdb-ripple-color="dark"
            @click="formulario"
          >
            Agregar
          </button>
        </form>
      </div>
    </nav>
  </div>
</template>
<script>
import { inject, ref } from "vue";
import * as moment from "moment";

export default {
  setup() {
    const todos = inject("todos");
    const texto = ref("");
    const formulario = () => {
      if (texto.value === "") {
        console.log("Esta vacio");
        return;
      }
      const todo = {
        texto: texto.value,
        estado: false,
        id: Date.now(),
        fechaCreado: moment().format("LLLL"),
      };
      todos.value.push(todo);
      //console.log(todos.value);
      texto.value = "";
    };
    return { formulario, texto };
  },
};
</script>
