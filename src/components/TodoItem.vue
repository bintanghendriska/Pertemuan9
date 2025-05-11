<template>
  <div class="todo-item">
    <slot></slot>
    {{ task }}
    <button @click="$emit('delete-task')">Hapus</button>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: String,
      required: true
    }
  }
}
</script>

<style>
.todo-item {
  display: flex;
  justify-content: space-between;
  margin: 0.5em 0;
  padding: 0.5em;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
