<template>

  <section class="src-components-recursos">
    <h2 class="mt-4">Usuarios cargados en mockapi.io</h2>

    <h3 class="mt-4">Utilizando them/catch</h3>
    <div v-if="rowsThemCatch.length" class="table-responsive">
      <table class="table">
        <tr>
          <th>Nombre</th>
          <th>Edad</th>
          <th>Email</th>
        </tr>
        <tr v-for="(row,index) in rowsThemCatch" :key="index" >
          <td>{{ row.name }}</td>
          <td>{{ row.age }}</td>
          <td>{{ row.email }}</td>
        </tr>
      </table> 
    </div>
    <div v-if="disabledAxiosThemCatch" class="spinner-border mt-3" role="status">
      <span class="sr-only">Cargando usuarios...</span>
    </div>
    <h3 v-else-if="!disabledAxiosThemCatch && rowsThemCatch.length == 0" class="alert alert-info mt-4">No hay usuarios disponibles.</h3>
    <br>


    <h3 class="mt-4">Utilizando async/await</h3>
    <div v-if="rowsAsyncAwait.length" class="table-responsive">
      <table class="table">
        <tr>
          <th>Nombre</th>
          <th>Edad</th>
          <th>Email</th>
        </tr>
        <tr v-for="(row,index) in rowsAsyncAwait" :key="index" >
          <td>{{ row.name }}</td>
          <td>{{ row.age }}</td>
          <td>{{ row.email }}</td>
        </tr>
      </table> 
    </div>
    <div v-if="disabledAxiosAsyncAwait" class="spinner-border mt-3" role="status">
      <span class="sr-only">Cargando usuarios...</span>
    </div>
    <h3 v-else-if="!disabledAxiosAsyncAwait && rowsAsyncAwait.length == 0" class="alert alert-info mt-4">No hay usuarios disponibles.</h3>
    <br>
  </section>
</template>

<script>

  export default  {
    name: 'src-components-recursos',
    props: [],
    mounted () {
      this.execAxiosAsyncAwait()
      this.execAxiosThemCatch()
    },
    data () {
      return {
        url: 'https://618ab08e34b4f400177c4823.mockapi.io/user',
        disabledAxiosAsyncAwait : false,
        rowsAsyncAwait : [],       
        disabledAxiosThemCatch : false,
        rowsThemCatch : [],        
      }
    },
    methods: {
      async execAxiosAsyncAwait() {
        this.rowsAsyncAwait = []
        this.disabledAxiosAsyncAwait = true

        try {
          let response = await this.axios(this.url)
          this.rowsAsyncAwait = response.data
          this.disabledAxiosAsyncAwait = false
        }
        catch(error) {
          console.error('Error AXIOS', error)
          this.disabledAxiosAsyncAwait = false
        }
      },
      execAxiosThemCatch() {
        this.rowsThemCatch = []
        this.disabledAxiosThemCatch = true

        this.axios(this.url)
        .then(response => {
          this.rowsThemCatch = response.data
          this.disabledAxiosThemCatch = false
        })
        .catch(error => {
            console.error('Error AXIOS', error)
            this.disabledAxiosThemCatch = false
        })
      },
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-recursos {

  }
</style>
