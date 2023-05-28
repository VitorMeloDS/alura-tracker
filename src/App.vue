<template>
  <main class="columns is-gapless is-multiline" :class="darkMode ? 'modo-escuro' : ''">
    <div class="column is-one-quarter">
      <LateralBar @alter-theme="alterThemes"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormTask @on-save="saveTaks"/>

      <div class="lista">
        <Taks :tasks="tasks" v-if="tasks[0]"/>
        <Box v-else>
          <p class="txt-default">Você não possui tarefa(s)!</p>
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Box from './components/Box.vue';
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
    Box,
  },
  data () {
    return {
      tasks: [] as Task[],
      darkMode: false
    }
  },
  methods: {
    saveTaks(task: Task) {
      this.tasks.push(task);
    },
    alterThemes(mode: boolean) {
      this.darkMode = mode;
    }
  }
});
</script>

<style acoped>
.lista {
  padding: 1.25rem;
}

.txt-default {
  display: flex;
  justify-content: center;
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
