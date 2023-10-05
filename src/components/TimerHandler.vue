<template>
  <section class="is-flex is-align-items-center is-justify-content-space-between">
    <TimerViewer :timeInSeconds="timeInSeconds"/>
    <ButtonModel @clicked="start" icon="fas fa-play" text="play" :disabled="isTimerRunning" />
    <ButtonModel @clicked="finish" icon="fas fa-stop" text="stop" :disabled="!isTimerRunning" />
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import TimerViewer from "./TimerViewer.vue"
import ButtonModel from "./ButtonModel.vue"

export default defineComponent({
  name: "TimerHandler",
  emits: ['onTimerFinishes'],
  components: { TimerViewer, ButtonModel },
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
