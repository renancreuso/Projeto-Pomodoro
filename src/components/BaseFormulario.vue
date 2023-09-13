<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
        />
      </div>
      <div class="column">
        <BaseTemporizador/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BaseTemporizador from "./BaseTemporizador.vue";


export default defineComponent({
  name: "BaseFormulario",
  components: {
    BaseTemporizador
},
  

 
});
</script>
