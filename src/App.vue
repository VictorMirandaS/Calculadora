<script>
import Calculadora from './components/Calculadora.vue';

export default {
  name: 'App',
  components: {
    Calculadora,
  },
};
</script>

<template>
  <div id="app">
    <Calculadora />
  </div>
</template>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  font-family: Arial, sans-serif;
  background-color: #eef2f5;
}
</style>
