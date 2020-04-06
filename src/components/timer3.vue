<template>
<div class="hero-body">
  
  <h2>{{title}}</h2>
  
  <div id="timer">
    <span id="minutes">{{ minutes }}</span>
    <span id="middle">:</span>
    <span id="seconds">{{ seconds }}</span>
  </div>

  <div id="buttons">
<!--     Start TImer -->
    <button 
      id="start" 
      class="mx-2" fab dark small color="primary"
      v-if="!timer"
      @click="startTimer">
        Start Timer
    </button>
<!--     Pause Timer -->
    <button 
      id="stop" 
      class="mx-2" fab dark small color="primary"
      v-if="timer"
      @click="stopTimer">
      Pause
    </button>
<!--     Restart Timer -->
    <button 
      id="reset" 
      class="mx-2" fab dark small color="primary"
      v-if="resetButton"
      @click="resetTimer">
       Reset
    </button>
  </div>

</div>
</template>


<script>
export default {
     data() { 
         return {
    timer: null,
    totalTime: (20 * 60),
    resetButton: false,
         };
  },
  // ========================
  methods: {
    startTimer: function() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
    },
    stopTimer: function() {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = true;
    },
    resetTimer: function() {
      this.totalTime = (20 * 60);
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
    },
    padTime: function(time) {
      return (time < 10 ? '0' : '') + time;
    },
    countdown: function() {
      if(this.totalTime >= 1){
        this.totalTime--;
      } else{
        this.totalTime = 0;
        this.resetTimer()
      }
    }
  },
  // ========================
  computed: {
    minutes: function() {
      const minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds: function() {
      const seconds = this.totalTime - (this.minutes * 60);
      return this.padTime(seconds);
    }
  }


}
</script>


<style scoped>

#message {
  color: #DDD;
  font-size: 20px;
}

#timer {
  font-size: 30px;

}

button {
    margin-top: 10px;
    border-radius: 5px;
    background-color: rgb(0, 99, 133);
    border: 0;
    color: white;
    padding: 7px 12px;
}

button:hover {
    background-color: rgb(0, 135, 180);
}

div#buttons {
    margin-left: 0;
    padding-left: 0;
}

</style>