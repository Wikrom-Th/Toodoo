<script lang="ts" setup>
  import Todos from './components/Todos.vue'
  import Timer from './components/Timer.vue'
</script>

<template>
  <h1>Toodoo</h1>
  <em>More than just a simple todo app</em>

  <div class="component">
    <h3>Todos</h3>
    <Todos />
  </div>

  <div class="component">
    <h3>Timer</h3>
    <Timer />
  </div>
</template>

<style>
.component {
  padding-top: 3em;
}
</style>