<template>
  <div class="box form">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Form for creating a new task">
        <input type="text" class="input" placeholder="What task do you want to start?" v-model="description" />
      </div>
      <div class="column">
        <TimerHandler @onTimerFinishes="finishTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import TimerHandler from "./TimerHandler.vue"

export default defineComponent({
  name: "FormPanel",
  emits: ['onSaveTask'],
  components: { TimerHandler },
  data() {
    return {
      description: ''
    }
  },
  methods: {
    finishTask(elapsedTime: number): void {
      this.$emit('onSaveTask', {
        timeInSeconds: elapsedTime,
        description: this.description
      })
      this.description = ''
    }
  }
})
</script>

<style>
.form {
  color: var(--primary-text);
  background-color: var(--primary-background);
}
</style>