<template>
  <div 
    class="box has-text-weight-bold"
    v-for="(task, index) in tasks" :key="index"
  >
    <div class="columns">
      <div class="column is-7">
        {{ task.describe }}
      </div>
      <div class="column">
        <Cronometro :tempSegunds="task.tempSegunds"/>
      </div>
    </div>
  </div>
</template>


<script lang="ts">
import { Task } from '@/interfaces/Task';
import { defineComponent, PropType } from 'vue';
import Cronometro from './Cronometro.vue';



export default defineComponent({
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Task',
  props: {
    tasks: {
      type: [] as PropType<Task>,
      require: true
    }
  },
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
