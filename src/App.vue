<script setup>
import { ref } from 'vue';

const timeInput = ref('');
const time = ref(0);
let countdown = null;

const startCountdown = () => {
    const parsedTime = parseInt(timeInput.value);
    
    if (isNaN(parsedTime) || parsedTime < 1 || parsedTime > 60) {
        alert("Please enter a valid number between 1 and 60.");
        return;
    }

    time.value = parsedTime;

    if (countdown) {
        clearInterval(countdown);
    }

    countdown = setInterval(() => {
        time.value--;
        if (time.value <= 0) {
            clearInterval(countdown);
            alert("Time's up! Have a great day!");
        }
    }, 1000);
};
</script>

<template>
  <div class="container">
    <h1>Countdown Timer</h1>
    <h2>By Victor Garza</h2>
    <h3>Enter from 1-60</h3>
    <input type="number" v-model="timeInput" placeholder="Enter seconds (1-60)" min="1" max="60" />
    <button @click="startCountdown">Start Countdown</button>
    <p>{{ time }}</p>
  </div>
</template>

<style scoped>
.container {
    text-align: center;
    font-family: Arial, sans-serif;
    margin-top: 50px;
}
input {
    padding: 8px;
    margin: 10px;
}
button {
    padding: 10px;
    background-color: blue;
    color: white;
    border: none;
    cursor: pointer;
}
p {
    font-size: 24px;
    font-weight: bold;
}
</style>

