<template>
  <div id="app" class="container-fluid mt-2">
    <div class="jumbotron">
      <h1>Trabajo Práctico n° 6</h1>
      <hr>
      <hr>
      <br>
    
      <Navbar />
      <router-view></router-view>
    </div>
  </div>
</template>

<script>

import Navbar from './components/Navbar.vue'

export default {
  name: 'App',
  components: {
    Navbar
  }
}
</script>

<style>
  #app {

  }

  .jumbotron {
    padding: 32px !important;
  }

  h1 {
    color: steelblue;
  }

</style>
