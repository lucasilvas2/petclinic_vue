<template>
  <div>
    <HeaderConsulta/>
    <div class="container pt-5">
      <div class="mx-auto mt-5">
        <h1 class="text-center">Consultas Rejeitadas</h1>

        <b-table striped hover :items="consultas" :fields="campos">
               
        </b-table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Consultas',
  data(){
    return{
      campos:[
        {key: 'pet.nome', sortable: true, label: 'Nome'},
        {key: 'data', sortable: true, label: 'Data'},
        {key: 'veterinario.nome', sortable: true, label: 'Veterinario'},
      ],
      consultas:[]     
                
    }  
  },
  mounted(){
    this.consumirConsultas()
  },
  methods:{
    consumirConsultas(){
      this.$axios.get('consulta/buscar/')
      .then(res=>{
        this.consultas = res.data;
        this.consultas = this.consultas.filter(c => c.statusConsulta == '2');
      })
      .catch(err =>{
        console.log(err);
      })
    }
  }
}
</script>