<template>
  <div id="app">
    <DifficultyScreen />
  </div>
</template>

<script>
import DifficultyScreen from './components/DifficultyScreen.vue'

export default {
  name: 'App',
  components: {
    DifficultyScreen
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #F0F0F0;
  height: 100vh;
}
body {
  padding: 0 !important;
  height: 100vh;
  background-color: #F0F0F0;
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
    monospace;
}
</style>
