<template>
  <div class="card">
    <div class="card-body bg-secondary shadow">
      <div class="d-flex justify-content-between text-light">
        <button
          role="button"
          class="btn btn-secondary "
          data-bs-toggle="button"
          autocomplete="off"
          @click="filtrar('actives')"
        >
          Active
        </button>
        <button
          role="button"
          class="btn btn-secondary"
          data-bs-toggle="button"
          autocomplete="off"
          aria-pressed="true"
          @click="filtrar('all')"
        >
          All
        </button>
        <button
          type="button"
          class="btn btn-secondary"
          data-bs-toggle="button"
          role="button"
          @click="filtrar('complete')"
        >
          Terminados
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { inject } from "vue";
export default {
  setup() {
    const estado = inject("estado");
    const filtrar = (valor) => {
      estado.value = valor;
      console.log(estado);
    };
    return { filtrar };
  },
};
</script>

<style></style>
