<template>
  <div class="countdown">
    <input v-model.number="timeInput" type="number" min="1" max="60" placeholder="Let's get started! Enter from (1-60)" />
    <button @click="startCountdown">Start Countdown</button>
    <h2>{{ timeLeft }}</h2>
  </div>

</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const timeInput = ref(null);
    const timeLeft = ref(null);
    let countdown = null;

    const startCountdown = () => {
      if (!timeInput.value || timeInput.value < 1 || timeInput.value > 60) {
        alert("Please enter a valid number between 1 and 60.");
        return;
      }
      
      timeLeft.value = timeInput.value;
      clearInterval(countdown);
      countdown = setInterval(() => {
        if (timeLeft.value > 0) {
          timeLeft.value--;
        } else {
          clearInterval(countdown);
          alert("Time's up!");
        }
      }, 1000);
    };

    return { timeInput, timeLeft, startCountdown };
  }
};
</script>

<style>
.countdown {
  text-align: center;
  font-family: Arial, sans-serif;
  margin-top: 20px;
}
</style>
