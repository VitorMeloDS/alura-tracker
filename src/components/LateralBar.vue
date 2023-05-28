<template>
  <header>
    <h1 class="has-background-white	header-h1">
      <img class="has-background-white img" src="../assets/logo.svg" alt="Imagem do alura tracker que redireciona o usuário para página inicial">
      <span class="header-text">Alura tracker</span>
    </h1>
    <button 
      class="button"
      @click="alterThemes"
    >
      {{ textButton }}
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'LateralBar',
  emits: ['alterTheme'],
  data() {
    return {
      darkMode: false
    }
  },
  computed: {
    textButton() {
      if (this.darkMode) return 'Desativar modo escuro';
      return 'Ativar modo escuro';
    }
  },
  methods: {
    alterThemes() {
      this.darkMode = !this.darkMode;
      this.$emit('alterTheme', this.darkMode);
    }
  }
});
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

button {
  margin-top: 15px;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}

.header-h1 {
  display: flex;
  align-items: center;
  padding: 5px 0;
  border-radius: 8px;
  cursor: pointer;
}

.header-h1 .img {
  border-radius: 50%;
  width: 20%;
  margin-left: 4vh;
}

.header-h1 .header-text {
  font-size: 22px;
  color: #0d3b66;
  margin-left: 2vh;
}
</style>
