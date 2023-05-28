<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <LateralBar/>
    </div>
    <div class="column is-three-quarter">
      <FormTask/>

      <div class="lista">
        <Taks/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormTask from './components/FormTask.vue';
import LateralBar from './components/LateralBar.vue';
import Taks from './components/Taks.vue';

export default defineComponent({
  name: 'App',
  components: {
    LateralBar,
    FormTask,
    Taks,
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
</style>
