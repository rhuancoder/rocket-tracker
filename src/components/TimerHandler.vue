<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <TimerViewer :timeInSeconds="timeInSeconds" />
    <button class="button" @click="start" :disabled="isTimerRunning">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finish" :disabled="!isTimerRunning">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import TimerViewer from "./TimerViewer.vue"

export default defineComponent({
  name: "TimerHandler",
  emits: ['onTimerFinishes'],
  components: { TimerViewer },
  data() {
    return {
      timeInSeconds: 0,
      timer: 0,
      isTimerRunning: false
    }
  },
  methods: {
    start() {
      this.isTimerRunning = true
      this.timer = setInterval(() => {
        this.timeInSeconds += 1
      }, 1000)
    },
    finish() {
      this.isTimerRunning = false
      clearInterval(this.timer)
      this.$emit('onTimerFinishes', this.timeInSeconds)
      this.timeInSeconds = 0
    }
  }
})
</script>
