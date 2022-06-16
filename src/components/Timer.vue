<script lang="ts" setup>
import { ref } from 'vue'

var intervalID: number | undefined
const timer = ref(25)

const running = ref(false)
const invalidTime = ref(false)

function onInput(e) {
  if(running.value) {
  return
  }

  if(isNaN(e.target.value)) {
  invalidTime.value = true
  return
  } 
  
  invalidTime.value = false
  timer.value = e.target.value
  e.target.value = ""
}

function countdown() {
  if(timer.value > 0) {
    running.value = true
  }
  else { 
    running.value = false
  }

  if(!running.value) {
    clearInterval(intervalID)
    return
  }

  timer.value -= 1
}

function startTimer() {
  intervalID = setInterval(countdown, 1000)
}
</script>

<template>
  <div>
    <h1>Timer</h1>
    Time: 
    <input :value="timer" @input="onInput">
  </div>
  <div>
    <button @click="startTimer">Start</button>
  </div>
  <h2 :class="{ error: invalidTime } ">{{ invalidTime ? 'Warning: time must be a number' : timer }}</h2>
</template>

<style>
.error {
    color: red;
}
</style>