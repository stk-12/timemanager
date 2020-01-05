<template>
  <div id="app">
    <div class="tasks">
      <Task />
    </div>
    <!-- <div class="add">
      <div class="add__inner">
        <div class="add__input">
          <input type="text">
          <button class="add__input__btn">ADD</button>
        </div>
        <button class="add__btn"><span>Add Task</span></button>
      </div>
    </div> -->
    <AddTask />
  </div>
</template>

<script>
import Task from './components/Task.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'app',
  components: {
    Task,
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
.tasks {
  padding: 20px;
}
</style>
