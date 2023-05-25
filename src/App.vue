<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <LateralBar/>
    </div>
    <div class="column is-three-quarter">
      <FormTask/>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormTask from './components/FormTask.vue';
import LateralBar from './components/LateralBar.vue';

export default defineComponent({
  name: 'App',
  components: {
    LateralBar,
    FormTask,
  }
});
</script>

<style>

</style>
