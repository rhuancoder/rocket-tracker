<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <FormPanel @onSaveTask="saveTask" />
      <div class="tasks">
        <TaskModel v-for="(task, index) in tasks" :key="index" :task="task"/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import SideBar from './components/SideBar.vue'
import FormPanel from './components/FormPanel.vue'
import TaskModel from './components/TaskModel.vue'
import ITask from './interfaces/ITask'

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    FormPanel,
    TaskModel
  },
  data() {
    return {
      tasks: [] as ITask[]
    }
  },
  methods: {
    saveTask(task: ITask) {
      this.tasks.push(task)
    }
  }
})
</script>

<style>
.tasks {
  padding: 1.25rem;
}
</style>
