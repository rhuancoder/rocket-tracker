<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">
        Task description
      </div>
      <div class="column">
        <TimerViewer :timeInSeconds="15"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TimerViewer from './TimerViewer.vue'

export default defineComponent({
  name: 'TaskModel',
  components: { TimerViewer }
})
</script>

<style scoped>
.box {
  background: #FAF0CA;
}
</style>