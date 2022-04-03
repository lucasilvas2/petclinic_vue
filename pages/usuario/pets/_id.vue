<template>
  <div>
    <HeaderUsuario/>
    <div class="container pt-5">
      <h4 class="mt-4 mb-2"> <nuxt-link to="/usuario/pets/"> Voltar aos pets </nuxt-link></h4>
      <hr>
      <div class="mt-3 mb-5 ml-2 mr-2">
        <b-row>
            <b-col>
                <b-row class="mt-2">
                    <h1 class="pt-2"> {{pet.nome}} </h1>
                </b-row>
                <b-row class="mt-2">
                    <span>Aniversário: {{pet.aniversario}}</span>
                </b-row>
                <b-row class="mt-2">
                    <span>Dono: {{pet.dono.nome}}</span>
                </b-row>
                <b-row>
                    <b-button size="sm" class="mr-2" variant="info" to="/usuario/pets/consulta/1" >
                      Solicitar Consulta
                    </b-button>
                    <b-button size="sm" class="mr-2" variant="warning" :to="`/usuario/pets/editar/${this.pet.idPet}`" >
                      Editar
                    </b-button>
                    <b-button size="sm" class="mr-2" @click="excluir" variant="danger" >
                        Excluir
                    </b-button>
                </b-row>
                
            </b-col>
        </b-row>
      </div>
    
    </div>
  </div>
</template>

<script>
export default {
  name: 'Pets',
  data(){
    return{ 
      pet: {
        idPet: 0,
        nome: '',
        aniversario: '',
        dono: {
          nome: ''
        }
      }                      
    }    
  },
  mounted(){
    this.consumirPets()
  },
  methods:{
    consumirPets(){
      this.$axios.get(`pet/buscar/${this.$route.params.id}`)
      .then(res =>{
        this.pet = res.data
      })
      .catch(err => {
        console.log(err)
      })
    },
    excluir(){
      this.$axios.delete(`pet/deletar/${this.$route.params.id}`)
      .then(res =>{
        this.$router.push("/usuario/pets");
        console.log("Pet excluido");
      })
      .catch(err =>{
        console.log(err);
      })
    }
  }
}
</script>