<template>
  <div class="task">
    <p class="task__name">{{ taskName }}</p>
    <div class="timer">
      <div class="timer__time">
        <!-- <p class="timer__time-total">{{ timeTotal }}</p> -->
        <p class="timer__time-state">{{ timeState }}</p>
      </div>
      <div class="timer__button">
        <button class="timer__button-start" v-on:click="countStart" v-if="!isMeasuring">start</button>
        <button class="timer__button-stop" v-on:click="countStop" v-if="isMeasuring">stop</button>
      </div>
    </div>
    <pre>{{ $data }}</pre>
  </div>
</template>

<script>
export default {
  name: 'task',
  data(){
    return {
      taskName: 'タスク名',
      isMeasuring: false,
      timeTotal: 0,
      timeState: '00:00:00',
      startTime: 0,
      //time: ''
      timerId: ''
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
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
