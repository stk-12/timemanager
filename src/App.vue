<template>
  <div id="app">
    <TaskList />
    <AddTask />
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'app',
  components: {
    TaskList,
    AddTask
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
</style>
