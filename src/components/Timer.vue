<script lang="ts" setup>
import { ref } from 'vue'

var intervalID: number | undefined

const timerText = ref("25")
const timer = ref(25)

const running = ref(false)
const invalidTime = ref(false)

function onInput(e) {
  timerText.value = e.target.value

  if(running.value) {
  return
  }

  if(isNaN(e.target.value)) {
  invalidTime.value = true
  return
  } 
  
  invalidTime.value = false
  timer.value = timerText.value as unknown as number
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
    Time: 
    <input :value="timerText" @input="onInput">
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