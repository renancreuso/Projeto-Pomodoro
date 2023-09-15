<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro':modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <BaseFormulario @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <BaseTarefa
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
      </div>
      <BaseBox v-if="listaVazia">
        você não está muito Produtivo hoje =(
      </BaseBox>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import BaseFormulario from "./components/BaseFormulario.vue";
import BaseTarefa from "./components/BaseTarefa.vue";
import ITarefa from "./interface/ITarefa";
import BaseBox from "./components/BaseBox.vue";

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    BaseFormulario,
    BaseTarefa,
    BaseBox,
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    };
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
    trocarTema(modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  },
  computed:{
    listaVazia() :boolean{
      return this.tarefas.length === 0
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
main {
  --bg-primario: #fff;
  --texto-primario: #000;
}
main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
