<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <LateralBar/>
    </div>
    <div class="column is-three-quarter">
      <FormTask @on-save="saveTaks"/>

      <div class="lista">
        <Taks :tasks="tasks"/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormTask from './components/FormTask.vue';
import LateralBar from './components/LateralBar.vue';
import Taks from './components/Taks.vue';
import { Task } from './interfaces/Task';

export default defineComponent({
  name: 'App',
  components: {
    LateralBar,
    FormTask,
    Taks,
  },
  data () {
    return {
      tasks: [] as Task[]
    }
  },
  methods: {
    saveTaks(task: Task) {
      this.tasks.push(task);
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
</style>
