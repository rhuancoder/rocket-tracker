<template>
  <BoxModel>
    <div class="columns">
      <div class="column is-7">
        {{ task.description || 'Task without description' }}
      </div>
      <div class="column">
        <TimerViewer :timeInSeconds="task.timeInSeconds" />
      </div>
    </div>
  </BoxModel>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import TimerViewer from './TimerViewer.vue'
import ITask from '../interfaces/ITask'
import BoxModel from './BoxModel.vue'

export default defineComponent({
  name: 'TaskModel',
  components: { TimerViewer, BoxModel },
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true
    }
  }
})
</script>