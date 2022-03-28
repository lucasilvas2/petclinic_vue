<template>
  <div>
    <div class="container pt-5">
        <h1 class="text-center"> Consulta</h1>
        <b-form @submit.prevent="onSubmit">

            <b-form-group id="group1" label="Data:" label-for="input1">
                <b-form-input type="date" id="input1" v-model="form.data" placeholder="Insira a data da consulta" required>
                </b-form-input>
            </b-form-group>

            <b-form-group id="group2" label="Veterinário:" label-for="input2">
                <b-form-select id="input2" v-model="veterinario" placeholder="Escolha o ID do Veterinário" :options="opcoes" required>
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
            form:{
                data: '',
            },
            opcoes:[
                {value: null, text: "Escolha um veterinário"},
                {value: 1, text: "Lucas"},
                {value: 2, text: "Marcos"},
                {value: 3, text: "Pedro"}
            ]
        }
    },
    methods:{
        onSubmit(){
            console.log(this.form);
            this.$router.push("/usuario/pets");
        }
    }  
}
</script>