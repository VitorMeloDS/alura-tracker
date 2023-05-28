<template>
  <div class="box formulario">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model.trim="describe"
        >
      </div>
      <div class="column">
        <Timer @on-finished="finished"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Task } from '@/interfaces/Task';
import { defineComponent } from 'vue';
import Timer from './Timer.vue';

export default defineComponent({
  name: 'FormTask',
  emits: ['onSave'],
  data() {
    return {
      describe: '',
      task: {} as Task
    }
  },
  components: {
    Timer,
  },
  methods: {
    finished(time: number) {
      this.task = {
        tempSegunds: time,
        describe: this.describe
      };

      this.$emit('onSave', this.task);
    }
  }
})
</script>

<style scoped>
.forms {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.formulario {
  color: var(--texto-primario);
  background-color: var(--bg-primario);
  box-shadow: 0 4px 2px -2px rgba(124, 125, 126, 0.348);
}
</style>
