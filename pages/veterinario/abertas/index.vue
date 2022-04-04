<template>
  <div>
    <HeaderConsulta/>
    <div class="container pt-5">
      <div class="mx-auto mt-5">
        <h1 class="text-center">Consultas Abertas</h1>

        <b-table striped hover :items="consultas" :fields="campos">
            <template #cell(Ações)="row">
                <b-button size="sm" class="mr-2" @click="aceitarConsultas(row.item)"> 
                    Aceitar
                </b-button>
                <b-button size="sm" class="mr-2" @click="rejeitarConsultas(row.item)"> 
                    Recusar
                </b-button>
            </template>
               
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
        {key: 'Ações', sortable: true, label: 'Ações'},
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
        this.consultas = this.consultas.filter(c => c.statusConsulta == '0');
      })
      .catch(err =>{
        console.log(err);
      })
    },
    aceitarConsultas(item){
      
      this.$axios.post('consulta/aceitar/'+ item.idConsulta)
      .then(res => {
        this.consumirConsultas()
      })
      .catch(err=>{
        console.log(err)
      })
    },
    rejeitarConsultas(item){
      this.$axios.post('consulta/rejeitar/'+ item.idConsulta)
      .then(res => {
        this.consumirConsultas()
      })
      .catch(err=>{
        console.log(err)
      })
    }
  }
}
</script>
