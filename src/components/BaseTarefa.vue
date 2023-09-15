<template>
  <BaseBox>
    <div class="colunns">
      <div class="collumns is-7">
        {{ tarefa?.descricao || "Tarefa sem Descrição" }}
      </div>
    </div>
    <div class="collumn">
      <BaseCronometro :tempo-em-segundo="tarefa?.duracaoEmSegundos" />
    </div>
  </BaseBox>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import BaseCronometro from "./BaseCronometro.vue";
import ITarefa from "@/interface/ITarefa";
import BaseBox from "./BaseBox.vue";

export default defineComponent({
  name: "BaseTarefa",
  components: { BaseCronometro, BaseBox },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      require: true,
    },
  },
});
</script>
