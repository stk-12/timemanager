<template>
  <div class="add">
      <div class="add__inner">
        <!-- <div class="add__input" v-if="isActive">
          <input type="text">
          <button class="add__input__button">ADD</button>
        </div> -->
        <!-- <button class="add__button" v-on:click="addTaskArea" v-if="!isActive"><span>Add Task</span></button> -->
        <button class="add__button" v-on:click="addTask" v-if="isActive"><span>Add Task</span></button>
      </div>
    </div>
</template>

<script>
export default {
  name: 'addTask',
  data(){
    return {
      isActive: true
    }
  },
  methods: {
    // addTaskArea: function(){
    //   this.isActive = true
    // }
    addTask: function(){
      
    }
  }
}
</script>

<style lang="scss" scoped>
.add {
  &__inner {
    padding: 20px;
  }
  &__input {
    display: flex;
    justify-content: center;
    input {
      background: #fff;
      padding: 15px;
      font-size: 16px;
    }
    &__button {
      background: #000;
      color: #fff;
      font-size: 16px;
      padding: 15px;
    }
  }
  &__button {
    background: #000;
    padding: 10px 15px;
    span {
      font-size: 16px;
      color: #fff;
      position: relative;
      padding: 0 0 0 15px;
      &::before {
        content: "+";
        display: block;
        position: absolute;
        left: 0;
        top: -4px;
        font-size: 20px;
      }
    }
  }
}
</style>
