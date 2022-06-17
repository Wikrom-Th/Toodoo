<script lang="ts" setup>
  import { ref } from 'vue'
  import Todos from './components/Todos.vue'
  import Timer from './components/Timer.vue'

  const currentMenu = ref("todos")

</script>

<template>
  <header>
    <h1>Toodoo</h1>
    <em>More than just a simple todo app</em>
  </header>

  <nav>
    <input type="radio" id="todos" value="todos" name="menu" v-model="currentMenu">
    <label for="todos">Todos</label>
  
    <input type="radio" id="timer" value="timer" name="menu" v-model="currentMenu">
    <label for="timer">Timer</label>
  </nav>

  <main>
    <div class="main-component" v-if="currentMenu === 'todos'"> 
      <h3>Todos</h3>
      <Todos />
    </div>
  
    <div class="main-component" v-if="currentMenu === 'timer'">
      <h3>Timer</h3>
      <Timer />
    </div>
  </main>

</template>

<style>

nav, .main-component {
  padding-top: 3em;
}
</style>