<template>
  <main class="columns is-gapless is-multiline dark-mode">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter content">
      <FormPanel @onSaveTask="saveTask" />
      <div class="tasks">
        <TaskModel v-for="(task, index) in tasks" :key="index" :task="task" />
        <BoxModel v-if="isListEmpty">
          No task has been created yet
        </BoxModel>
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
import BoxModel from './components/BoxModel.vue'

export default defineComponent({
  name: 'App',
  components: {
    SideBar,
    FormPanel,
    TaskModel,
    BoxModel
  },
  data() {
    return {
      tasks: [] as ITask[]
    }
  },
  computed: {
    isListEmpty() : boolean {
        return this.tasks.length === 0
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
main {
  --primary-background: #fff;
  --primary-text: #000;
}
main.dark-mode {
  --primary-background: #2b2d42;
  --primary-text: #ddd;
}
.content{
  background-color: var(--primary-background);
}
</style>
