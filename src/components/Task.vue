<template>
  <div class="task">
      <div class="task__inner">
        <div class="task__name">
          <input type="text" class="task__name-input" placeholder="Enter the task" v-model="taskName" v-if="isInput">
          <p class="task__name-text" v-if="!isInput">{{ taskName }}</p>
        </div>
        <div class="timer">
          <div class="timer__inner">
            <div class="timer__time">
              <p class="timer__time-state">{{ timeState }}</p>
            </div>
            <div class="timer__button">
              <button class="timer__button-start" v-on:click="countStart" v-if="!isMeasuring"><img src="/images/icon_play.svg" alt="play"></button>
              <button class="timer__button-stop" v-on:click="countStop" v-if="isMeasuring"><img src="/images/icon_stop.svg" alt="stop"></button>
            </div>
          </div>
        </div>
        <div class="menu">
          <div class="menu__inner">
            <button class="menu__button" v-on:click="showMenu"><img src="/images/icon_menu.svg" alt="menu"></button>
            <div class="menu__content" v-show="isShowMenu">
              <ul class="menu__lists">
                <li v-on:click="deleteTask">Delete Task</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'task',
  data(){
    return {
      taskName: '',
      isInput: true,
      isMeasuring: false,
      timeTotal: 0,
      timeState: '00:00:00',
      startTime: 0,
      //time: ''
      timerId: '',
      isShowMenu: false
    }
  },
  methods: {
    countStart: function(){
      this.startTime = Date.now();
      this.isMeasuring = true
      this.countTime();
      
    },
    countStop: function(){
      this.isMeasuring = false
      clearTimeout(this.timerId);
      this.timeTotal += Date.now() - this.startTime;
    },
    countTime: function(){
      
      const d = new Date(Date.now() - this.startTime + this.timeTotal);
      const h = String(d.getUTCHours()).padStart(2, '0');
      const m = String(d.getMinutes()).padStart(2, '0');
      const s = String(d.getSeconds()).padStart(2, '0');

      this.timeState = `${h}:${m}:${s}`;

      this.timerId = setTimeout(() => {
        this.countTime();
      }, 10);
    },
    showMenu: function(){
      if(!this.isShowMenu){
        this.isShowMenu = true
      } else {
        this.isShowMenu = false
      }
    },
    deleteTask: function(){
      this.$destroy();
      this.$el.parentNode.removeChild(this.$el);
    }
  }
}
</script>

<style lang="scss" scoped>
.task {
  background: #fff;
  & + .task {
    margin: 15px 0 0;
  }
  &__inner {
    padding: 20px 5px 20px 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  &__name {
    width: 80%;
    text-align: left;
    &-input {
      width: 100%;
      font-size: 18px;
    }
  }
}
.timer {
  &__inner {
    display: flex;
    align-items: center;
  }
  &__time {
    margin: 0 15px 0 0;
    p {
      font-size: 18px;
    }
  }
  &__button {
    button {
      cursor: pointer;
    }
    img {
      width: 30px;
      height: 30px;
    }
  }
}
.menu {
  width: 40px;
  &__inner {
    position: relative;
  }
  &__button {
    cursor: pointer;
    opacity: 0.3;
    &:hover {
      opacity: 1;
    }
    img {
      width: 20px;
    }
  }
  &__content {
    width: 120px;
    position: absolute;
    background: #fff;
    box-shadow: 0 0 10px 0 rgba(0,0,0,0.3);
    right: 0;
    top: 115%;
  }
  &__lists {
    li {
      padding: 8px 12px;
      list-style: none;
      cursor: pointer;
      &:hover {
        color: #ff0000;
      }
    }
  }
}
</style>
