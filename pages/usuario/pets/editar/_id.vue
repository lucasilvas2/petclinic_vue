<template>
  <div>
    <HeaderUsuario/>
    <div class="container pt-5">
        <h1 class="text-center"> Insira os dados do seu pet</h1>
        <b-form @submit.prevent="onSubmit">
            <b-form-group id="group1" label="Nome:" label-for="input1">
                <b-form-input id="input1" v-model="form.nome" placeholder="Insira o nome do pet" required>
                </b-form-input>
            </b-form-group>

            <b-form-group id="group2" label="Aniversario:" label-for="input2">
                <b-form-input type="date" id="input2" v-model="form.aniversario" placeholder="Insira o aniversário do pet" required>
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
    name: 'Pet',
    data(){
        return{
            form:{
                nome: '',
                aniversario: '',
                dono: {
                    idPessoa: 0
                }
            }
        }
    },
    mounted(){
        this.consumirPet()
    },
    methods:{
        consumirPet(){
            this.$axios.get(`/pet/buscar/${this.$route.params.id}`)
            .then(res =>{
                this.form = res.data
            })
        },
        onSubmit(){
            this.$axios.post('pet/cadastrar/'+this.form.dono.idPessoa,{
                idPet: this.$route.params.id,
                nome: this.form.nome,
                aniversario: this.form.aniversario
            })
            .then( res => {
                this.$router.push('/usuario/pets/');
            })
            .catch( err =>{
                console.log(err)
            });
        }
    }  
}
</script>