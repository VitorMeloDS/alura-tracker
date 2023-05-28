<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">

      </div>
      <div class="column">
        <Cronometro :tempSegunds="15"/>
      </div>
    </div>
  </div>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
import Cronometro from './Cronometro.vue';

export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Task',
  components: {
    Cronometro
  }
})
</script>

<style scoped>
.box {
  background-color: #FAF0CA;
}
</style>
