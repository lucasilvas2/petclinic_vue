<template>
  <div>
    <HeaderUsuario/>
    <div class="container pt-5">
      <div class="mx-auto mt-5">
        <h1 class="text-center">Consultas</h1>
        <b-table striped hover :items="consultas" :fields="campos">
             <template #cell(statusConsulta)="row">
                {{traduzirStatus(row.item.statusConsulta)}}
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
        {key: 'statusConsulta', sortable: true, label: 'Status'},
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
      })
      .catch(err =>{
        console.log(err);
      })
    },
    traduzirStatus(item){
      if(item == "0"){
        return 'Em aberto'
      }
      else if(item == '1'){
        return 'Aceita'
      }
      else if(item == '2'){
        return 'Rejeitda'
      }
      else{
        return 'Valor inválido'
      }
    }
  }    
}
</script>