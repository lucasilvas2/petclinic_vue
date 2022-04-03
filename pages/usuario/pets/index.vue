<template>
  <div>
    <HeaderUsuario/>
    <div class="container pt-5">
      <div class="mx-auto mt-5">
        <h1 class="text-center">Pets</h1>
        <b-row class="max-auto">
          <b-button size="sm" class="mr-2" to="/usuario/pets/criar">
            Adicionar novo pet
          </b-button>
        </b-row>
        <b-table striped hover :items="pets" :fields="campos">
            <template #cell(Ações)="row">
                <b-button size="sm" class="mr-2" :to="`/usuario/pets/${row.item.idPet}`"> 
                  Ver detalhes
                </b-button>
            </template>  
        </b-table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Pets',
  data(){
    return{
      campos:[
        {key: 'nome', sortable: true, label: 'Nome'},
        {key: 'dono.nome', sortable: true, label: 'Dono'},
        {key: 'Ações', sortable: true, label: 'Ações'},
      ],
      pets:[]     
                
    }      
  },
  mounted(){
    this.consumirPets()
  },
  methods:{
    consumirPets(){
      this.$axios.get('pet/buscar/')
      .then(res =>{
        this.pets = res.data;
      })
    }
  }
}
</script>
