<template>
  <div class="forms">
    <Cronometro :tempSegunds="tempSegunds"/>
      <button class="button" @click="started" :disabled="play">
        <span class="icon">
          <i class="fas fa-play"></i>
        </span>
        <span>iniciar</span>
      </button>
      <button class="button" @click="finished" :disabled="!play">
        <span class="icon">
          <i class="fas fa-stop"></i>
        </span>
        <span>parar</span>
      </button>
  </div>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
import Cronometro from './Cronometro.vue';

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Timer',
  emits: ['onFinished'],
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
      this.$emit('onFinished', this.tempSegunds);
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

</style>
