<template>
  <section>
    <strong class="display">
      {{ tempoDecorrido }}
    </strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Cronometro',
  props: {
    tempSegunds: {
      type: Number,
      required: true
    }
  },
  computed: {
    tempoDecorrido(): string {
      return new Date(this.tempSegunds * 1000).toISOString().split('T')[1].split('.')[0];
    }
  },
})
</script>

<style scoped>
.display {
  color: var(--texto-primario);
}
</style>
