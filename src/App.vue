<!-- src/App.vue -->
<template>
  <div id="app">
    <GuessingGame />
  </div>
</template>

<script>
import GuessingGame from './components/GuessingGame.vue';

export default {
  name: 'App',
  components: {
    GuessingGame
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<!-- Zuris Asignment -->
