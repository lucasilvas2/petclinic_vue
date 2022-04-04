<template>
  <div>
    <HeaderUsuario/>
    <div class="container pt-5">
        <h1 class="text-center"> Cadastrar usuário</h1>
        <b-form @submit.prevent="onSubmit">
            <b-form-group id="group1" label="Nome:" label-for="input1">
                <b-form-input id="input1" v-model="form.nome" placeholder="Insira o nome do usuario" required>
                </b-form-input>
            </b-form-group>

            <b-form-group id="group2" label="Email:" label-for="input2">
                <b-form-input  id="input2" v-model="form.email" placeholder="Insira o seu email" required>
                </b-form-input>
            </b-form-group>

            <b-form-group id="group3" label="Telefone:" label-for="input3">
                <b-form-input id="input3" v-model="form.telefone" placeholder="Insira o seu telefone" required>
                </b-form-input>
            </b-form-group>

            <b-form-group id="group4" label="Endereço:" label-for="input4">
                <b-form-input id="input4" v-model="form.endereco" placeholder="Insira o seu endereço" required>
                </b-form-input>
            </b-form-group>

            <b-button type="submit" variant="primary">
                Submit
            </b-button>
      </b-form>
    </div>
  </div>
</template>

<script>
export default {
    name: 'CriarDono',
    data(){
        return{
            form:{
                nome: '',
                email: '',
                telefone: '',
                endereco: ''
            }
        }
    },
    methods:{
        onSubmit(){
            console.log(this.form);
            this.$axios.post("dono/cadastrar/", {
                nome: this.form.nome,
                email:  this.form.email,
                telefone: this.form.telefone,
                endereco: this.form.endereco
            })
            .then(res =>{
                this.$router.push("/usuario/pets");
            })
            .catch(err =>{
                console.log(err);
            })
        }
    }  
}
</script>