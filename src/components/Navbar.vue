<template>

  <section class="src-components-navbar">
  <nav class="navbar navbar-expand-md navbar-dark bg-dark">    
      <router-link to="/">
        <a class="navbar-brand" href="#">Inicio</a>
      </router-link>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link to="/formulario">
              <a class="nav-link" href="#">Formulario</a>
            </router-link>
          </li>

          <li class="nav-item">
            <router-link to="/usuarios">
              <a class="nav-link" href="#">Usuarios</a>
            </router-link>
          </li>
        </ul>
      </div>
    </nav>


  </section>

</template>

<script>

  export default  {
    name: 'src-components-navbar',
    props: [],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-navbar {

  }
</style>
