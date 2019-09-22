<template>
  <div id="app" class="container">
    <grafico></grafico>
    <hr>
    <tabela></tabela>
  </div>
</template>

<script>
import grafico from './components/grafico.vue';
import tabela from './components/tabela.vue'

export default {
  name: 'app',
  components: {
    grafico,
    tabela
  }
}
</script>

<style>

</style>
