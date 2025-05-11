<template>
  <div class="app">
    <h1>My To-do List</h1>
    
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Tambahkan tugas baru..." />

    <div v-if="tasks.length">
      <TodoItem
        v-for="(task, index) in tasks"
        :key="index"
        :task="task"
        @delete-task="deleteTask(index)"
      >
        <template #default>
          <span>📝</span>
        </template>
      </TodoItem>
    </div>
    <p v-else>Tidak ada tugas.</p>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue'

export default {
  components: { TodoItem },
  data() {
    return {
      newTask: '',
      tasks: []
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push(this.newTask.trim())
        this.newTask = ''
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>

<style>
.app {
  max-width: 500px;
  margin: auto;
  padding: 1em;
}
</style>
