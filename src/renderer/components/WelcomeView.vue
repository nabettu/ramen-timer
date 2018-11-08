<template>
  <v-container grid-list-md text-xs-center>
    <v-layout row wrap>
      <v-flex xs12 align-center justify-center>
        <v-progress-circular :rotate="-90" :size="maxTime" :width="15" :value="time" color="primary" >{{minutes + "::" + seconds}}</v-progress-circular>
      </v-flex>
      <v-flex xs12>
        <v-btn color="success" @click="start()" v-show="!isRunning">start</v-btn>
        <v-btn color="error" @click="stop()" v-show="isRunning">stop</v-btn>
        <v-btn color="warning" @click="reset()" v-show="time != maxTime">reset</v-btn>
      </v-flex>
    </v-layout>
    </v-container>
</template>

<script>
export default {
  name: "timer-page",
  data: function() {
    return {
      time: 2,
      isRunning: false,
      maxTime: 180
    };
  },
  computed: {
    minutes: function() {
      return parseInt(this.time / 60);
    },
    seconds: function() {
      return ("00" + (this.time % 60)).slice(-2);
    }
  },
  methods: {
    start: function() {
      this.isRunning = true;
      this.timer = setInterval(() => {
        if (this.isRunning && this.time > 0) {
          this.time--;
        } else if (this.isRunning && this.time < 1) {
          this.timeOut();
        }
      }, 1000);
    },
    timeOut: function() {
      this.isRunning = false;
      this.time = this.maxTime;
      clearInterval(this.timer);
      new Notification("時間です");
    },
    reset: function() {
      this.time = this.maxTime;
      clearInterval(this.timer);
    },
    stop: function() {
      this.isRunning = false;
      clearInterval(this.timer);
    }
  }
};
</script>

<style scoped>
</style>
