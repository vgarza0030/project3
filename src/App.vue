<template>
  <div class="container">
    <h1>Countdown Timer</h1>
    <h2>By Victor Garza</h2>
    <h3>Enter from 1-60</h3>
    <input type="number" v-model.number="timeInput" placeholder="Enter seconds (1-60)" min="1" max="60">
    <button @click="startCountdown">Start Countdown</button>
    <p>{{ timeLeft }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timeInput: null,
      timeLeft: null,
      countdown: null,
    };
  },
  methods: {
    startCountdown() {
      if (isNaN(this.timeInput) || this.timeInput < 1 || this.timeInput > 60) {
        alert("Please enter a valid number between 1 and 60.");
        return;
      }
      
      this.timeLeft = this.timeInput;
      
      if (this.countdown) clearInterval(this.countdown);
      
      this.countdown = setInterval(() => {
        this.timeLeft--;
        if (this.timeLeft <= 0) {
          clearInterval(this.countdown);
          alert("Time's up! Have a great day!");
        }
      }, 1000);
    },
  },
};
</script>


<style scoped>
.container {
  text-align: center;
}
</style>