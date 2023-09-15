<template>
    <section>
      <strong class="display">
        {{ tempoDecorrido }}
      </strong>
    </section>
  </template>

<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent ({
    name:'BaseCronometro',

    data(){
        return{

        }
    },
    props:{
        tempoEmSegundo:{
            type: Number,
            default: 0     
        }
    },
    computed: {
    tempoDecorrido(): string {
      const horas = Math.floor(this.tempoEmSegundo / 3600);
      const minutos = Math.floor((this.tempoEmSegundo % 3600) / 60);
      const segundos = this.tempoEmSegundo % 60;

      const horasFormatadas = horas.toString().padStart(2, "0");
      const minutosFormatados = minutos.toString().padStart(2, "0");
      const segundosFormatados = segundos.toString().padStart(2, "0");

      return `${horasFormatadas}:${minutosFormatados}:${segundosFormatados}`;
    },
  },

})
    

</script>

<style scoped>
.display {
  color: var(--texto-primario);
}
</style>