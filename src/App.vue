<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter">
        <BaseFormulario/>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import BaseFormulario from './components/BaseFormulario.vue';


export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    BaseFormulario
}
});
</script>

<style>

</style>
