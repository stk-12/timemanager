<template>
  <div id="app">
    <div class="tasks">
      <Task />
    </div>
    <button class="add__btn"><span>Add Task</span></button>
  </div>
</template>

<script>
import Task from './components/Task.vue'

export default {
  name: 'app',
  components: {
    Task
  }
}
</script>

<style lang="scss" scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.tasks {
  padding: 20px;
}
</style>
