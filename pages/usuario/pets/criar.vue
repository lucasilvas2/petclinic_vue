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

            <b-form-group id="group3" label="Dono:" label-for="input3">
                <b-form-select id="input3" v-model="form.id_dono" :options ="options" required>
                </b-form-select>
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
    name: 'Criar',
    data(){
        return{
            form:{
                nome: '',
                aniversario: '',
                id_dono: null
            },
            options:[
                {value: null, text: "Escolha o dono do pet"}
            ],
            donos:[]
        }
    },
    mounted(){
        this.consumirDonos()
    },
    methods:{
        consumirDonos(){
            this.$axios.get('dono/buscar/')
            .then(res =>{
                this.donos = res.data
                this.donos.forEach((value, index) => {
                    this.options.push({
                        value: value.idPessoa,
                        text: value.nome
                    })
                })
            })
        },
        onSubmit(){
            console.log(this.form);
            this.$axios.post('pet/cadastrar/'+this.form.id_dono,{
                nome: this.form.nome,
                aniversario: this.form.aniversario
            })
            .then( res => {
                this.$router.push('/usuario/pets/');
            })
            .catch( err =>{
                console.log(err)
            })
        }
    }  
}
</script>