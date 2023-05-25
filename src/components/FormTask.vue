<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?">
      </div>
      <div class="column">
        <div class="forms">
          <Cronometro :tempSegunds="tempSegunds"/>
          <button class="button" @click="started" :disabled="play">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button class="button" @click="finished">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Cronometro from './Cronometro.vue';

export default defineComponent({
  name: 'FormTask',
  data() {
    return {
      tempSegunds: 0,
      cronometro: 0,
      play: false
    }
  },
  methods: {
    started() {
      if (this.tempSegunds == 0) {
        this.play = true;
        this.cronometro = setInterval(() => {
          ++this.tempSegunds;
        }, 1000);
      }
    },
    finished() {
      this.play = false;
      this.tempSegunds = 0;
      clearInterval(this.cronometro);
    }
  },
  components: {
    Cronometro,
  }
})
</script>

<style scoped>
.forms {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
