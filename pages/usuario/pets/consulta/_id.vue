<template>
  <div>
    <HeaderUsuario/>
    <div class="container pt-5">
        <h1 class="text-center"> Consulta</h1>
        <b-form @submit.prevent="onSubmit">

            <b-form-group id="group1" label="Data:" label-for="input1">
                <b-form-input type="date" id="input1" v-model="form.data" placeholder="Insira a data da consulta" required>
                </b-form-input>
            </b-form-group>

            <b-form-group id="group2" label="Veterinário:" label-for="input2">
                <b-form-select id="input2" v-model="veterinario" :options="opcoes" required>
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
            veterinario: null,
            vet: [],
            form:{
                data: '',
                statusConsulta: 0
            },
            opcoes:[
                {value: null, text: "Escolha um veterinário"}
            ]
        }
    },
    mounted(){
        this.consumirVet()
    },
    methods:{
        consumirVet(){
            this.$axios.get('/veterinario/buscar/')
            .then(res=>{
                this.vets = res.data
                this.vets.forEach((value, index) =>{
                    this.opcoes.push({
                        value: value.idPessoa,
                        text: value.nome
                    })
                })
            })
        },
        onSubmit(){
            console.log(this.form);
            console.log(this.veterinario);
            this.$axios.post("consulta/cadastrar/"+this.veterinario+"/"+this.$route.params.id, {
                data: this.form.data,
                statusConsulta: this.form.statusConsulta
            })
            .then(res =>{
                this.$router.push("/usuario/pets");
            })
            .catch(err =>{
                console.log(err)
            })
            
        }
    }  
}
</script>