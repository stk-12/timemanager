<template>
  <div class="task-list">
    <Task></Task>
    <Task></Task>
  </div>
</template>

<script>
import Task from './Task.vue'

export default {
  name: 'taskList',
  components: {
    Task
  }
}
</script>

<style lang="scss" scoped>
.task-list {
  padding: 20px;
}
</style>
