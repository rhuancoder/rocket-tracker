<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Form for creating a new task">
        <input type="text" class="input" placeholder="What task do you want to start?" />
      </div>
      <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">
          <TimerViewer :timeInSeconds="timeInSeconds" />
          <button class="button" @click="start">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button class="button" @click="finish">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import TimerViewer from "./TimerViewer.vue"

export default defineComponent({
    name: "FormPanel",
    components: { TimerViewer },
    data() {
        return {
            timeInSeconds: 0,
            timer: 0
        };
    },
    methods: {
        start() {
            this.timer = setInterval(() => {
                this.timeInSeconds += 1;
            }, 1000);
        },
        finish() {
            clearInterval(this.timer);
        }
    }
})
</script>

<style></style>