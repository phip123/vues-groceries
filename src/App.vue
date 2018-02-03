<template>
  <div id="app">
    <groceries/>

  </div>
</template>

<script>
import groceries from './components/Groceries'

export default {
  name: 'App',
  components: {
    groceries
  }
}
</script>

<style>
  #app {
    text-align: center;
  }
</style>
