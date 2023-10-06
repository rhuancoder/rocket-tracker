<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <FormPanel />
      <div class="tasks">
        <TaskModel />
        <TaskModel />
        <TaskModel />
        <TaskModel />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import SideBar from './components/SideBar.vue'
import FormPanel from './components/FormPanel.vue'
import TaskModel from './components/TaskModel.vue'

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    FormPanel,
    TaskModel
  }
})
</script>

<style>
.tasks {
 padding: 1.25rem;
}
</style>
