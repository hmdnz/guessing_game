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
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: linear-gradient(135deg, #89f7fe 0%, #66a6ff 100%);
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
