<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">
        {{ task.description }}
      </div>
      <div class="column">
        <TimerViewer :timeInSeconds="task.timeInSeconds" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import TimerViewer from './TimerViewer.vue'
import ITask from '../interfaces/ITask';

export default defineComponent({
  name: 'TaskModel',
  components: { TimerViewer },
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true
    }
  }
})
</script>

<style scoped>
.box {
  background: #FAF0CA;
}
</style>