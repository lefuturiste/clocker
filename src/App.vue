<template>
  <div id="app">
    <div class="container">
      <div class="clock-container">
        <div class="clock-content">
          <h1 class="clock-time">{{time}}</h1>
          <h3 class="clock-date">{{date}}</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
var moment = require('moment');
export default {
  name: 'app',
  data () {
    return {
      time: "",
      date: ""
    }
  },
  created () {
    this.newLoop()
  },
  methods: {
    newLoop: function () {
      setTimeout(() => {
        this.fetchDateTime()
        this.newLoop()
      }, 1000)
    },
    fetchDateTime: function() {
     var now = moment()
     moment.locale('fr')
     this.date = now.format('dddd MMMM YYYY')
     this.time = now.format('HH:mm:ss')
    }
  }
}
</script>

<style lang="scss">
   @import url('https://fonts.googleapis.com/css?family=Lato');
  @import '../node_modules/normalize.css/normalize.css';
  .container {
    font-family: 'Lato', sans-serif;
    background-image: linear-gradient(to right bottom, #16a085, #09a47e, #09a876, #17ab6c, #27ae60);
    color: white;
    height: 100vh;
    width: 100%;
    display: flex;
    flex-direction: column;
    .clock-container {
      display: flex;
      height: 80vh;
      justify-content: center;
      align-items: center;
    }
  }
  .clock-content {
    text-align: center;
    .clock-time {
      font-size: 5em;
    }
    .clock-date {
      font-size: 1.8em;
    }
  }
</style>
