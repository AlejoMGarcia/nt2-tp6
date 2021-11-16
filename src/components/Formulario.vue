<template>

  <section class="src-components-formulario">
    <vue-form :state="formstate" @submit.prevent="cargarRegistro()">

      <validate tag="div" class="mt-4">
        <label for="name">Nombre</label>
        <input type="text" 
          id="name" 
          name="name" 
          class="form-control"
          v-model.trim="formData.name" 
          :minlength="minlength" 
          :maxlength="maxlength"
          required
          autocomplete="off">

        <field-messages name="name" show="$dirty">
          <div slot="required" class="alert alert-danger mt-2">
            El nombre es requerido.
          </div>
          <div slot="minlength" class="alert alert-danger mt-2">
            El nombre debe tener al menos {{minlength}} caracteres.
          </div>
          <div v-if="nameHasMaxLength()" class="alert alert-danger mt-2">
            El nombre debe tener como máximo {{maxlength}} caracteres.
          </div>
        </field-messages>
      </validate>
      <br>

       
      <validate tag="div">
        <label for="age">Edad</label>
        <input type="number" 
          id="age" 
          name="age" 
          v-model.number="formData.age"
          class="form-control"
          required 
          :min="minAge" 
          :max="maxAge"
          autocomplete="off">

        <field-messages name="age" show="$dirty">
          <div slot="required" class="alert alert-danger mt-2">
            El nombre es requerido.
          </div>
          <div slot="min" class="alert alert-danger mt-2">
            La edad debe ser mayor a {{minAge}}.
          </div>
          <div slot="max" class="alert alert-danger mt-2">
            La edad no debe ser mayor a {{maxAge}}.
          </div>
        </field-messages>

      </validate>
      <br>


      
      <validate tag="div">
        <label for="email">Email</label>
        <input type="email" 
          id="email" 
          name="email" 
          placeholder="me@example.com"
          class="form-control"
          v-model.trim="formData.email" 
          required
          autocomplete="off">

        <field-messages name="email" show="$dirty">
          <div slot="required" class="alert alert-danger mt-2">
            El email es requerido.
          </div>
        </field-messages>
      </validate>
      <br>

      <button class="btn btn-success my-4" :disabled="formstate.$invalid" type="submit">Insertar en mockapi.io</button>

      </vue-form>

    
  </section>

</template>

<script>

  export default  {
    name: 'src-components-formulario',
    props: [],
    mounted () {

    },
    data () {
      return {
        url: 'https://618ab08e34b4f400177c4823.mockapi.io/user',
        minlength : 3,
        maxlength : 15,
        minAge : 18,
        maxAge : 120,
        formstate : {},
        formData : this.getInitialData(),
      }
    },
    methods: {
      getInitialData() {
        return {
          name : null,
          age : null,
          email : null,
        }
      },
      nameHasMaxLength() {
        return this.formData.name && this.formData.name.length == this.maxlength
      },
      cargarRegistro() {
        this.axios.post(this.url, this.formData)
            .then(response => this.articleId = response.data.id)
            .catch(error => {
              console.error('Error AXIOS', error)
            })

        this.formData = this.getInitialData()
        this.formstate._reset() 
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-formulario {

  }
</style>
