<template>
  <div>
    <HeaderUsuario/>
    <div class="container pt-5">
      <b-form @submit.prevent="onSubmit">
          <b-form-group id="group1" label="Email:" label-for="input1">
              <b-form-input id="input1" v-model="form.email" placeholder="Insira seu email" required>
              </b-form-input>
          </b-form-group>
          <b-button type="submit" variant="primary">
              Submit
          </b-button>
      </b-form>
      <h3> <nuxt-link to="/registroVeterinario"> Cadastre-se </nuxt-link> </h3>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Login',
    data(){
        return{
            form:{
                email: ''
            }
        }
    },
    methods:{
        onSubmit(){
            console.log(this.form);
            this.$router.push("/veterinario/abertas/");
        }
    }  
}
</script>