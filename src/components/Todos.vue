<script lang="ts" setup>
import { ref } from 'vue'

let id = 0

const msg = ref('Todo')
const inputTodo = ref('')
var todos = ref([
  {id: id++, text:"Test", done: false}
])

function addTodo() {
  todos.value.push({id:id++, text: inputTodo.value, done: false})
  inputTodo.value = ""
}

function removeDone() {
  todos.value = todos.value.filter(todo => !todo.done)
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.done">
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
    </li>
  </ul>
  <form @submit.prevent="addTodo">
      <input v-model="inputTodo">
      <button>Add</button>
  </form>
  <button @click="removeDone">Remove Done</button>
</template>

<style>
  .done {
    opacity: 0.4;
  }
  ul {
    list-style: none;
  }
</style>