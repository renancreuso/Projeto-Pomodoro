<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <!-- passando valor para o filho, componente possui propriedade chamada tempoEmSegundo que atribuimos tempoEmSegundo -->
    <BaseCronometro :tempoEmSegundo="tempoEmSegundo" />

    <button @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>

    <button @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BaseCronometro from "../components/BaseCronometro.vue";

export default defineComponent({
  name: "BaseTemporizador",
  emits:['aoTemporizadorFinalizado'],
  components: {
    BaseCronometro,
  },

  data() {
    return {
      tempoEmSegundo: 0,
      cronometro: 0,
      cronometroRodando: false,
    };
  },

    methods: {
      iniciar() {
        this.cronometroRodando = true;
        this.cronometro = setInterval(() => {
          this.tempoEmSegundo += 1;
        }, 1000);
        console.log("Iniciando");
      },
      finalizar() {
        this.cronometroRodando = false;
        clearInterval(this.cronometro);
        console.log("Finalizando");
        this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundo)
        this.tempoEmSegundo = 0

      },
    },
  
});
</script>
