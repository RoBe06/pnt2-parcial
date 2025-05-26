<template>
  <div id="app" class="container">
    <h1 class="my-4">Parcial</h1>
    <FormularioComponente />
    <p>Respuestas: {{ respuestas }}</p>
  </div>
</template>

<script>
import FormularioComponente from './components/FormularioComponente.vue';

export default {
  name: 'App',
  components: {
    FormularioComponente
  },
  data() {
    return {
      respuestas: {
        1: 'c',
        2: 'c',
        3: 'a'
      }
    };
  }
};
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>