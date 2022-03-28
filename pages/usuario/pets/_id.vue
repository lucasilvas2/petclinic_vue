<template>
  <div>
    <div class="container pt-5">
      <h4 class="mt-4 mb-2"> <nuxt-link to="/usuario/pets/"> Voltar aos pets </nuxt-link></h4>
      <hr>
      <div class="mt-3 mb-5 ml-2 mr-2">
        <b-row>
            <b-col>
                <b-row class="mt-2">
                    <h1 class="pt-2"> Rufus </h1>
                </b-row>
                <b-row class="mt-2">
                    <span>Aniversário: 15-02-2020</span>
                </b-row>
                <b-row class="mt-2">
                    <span>Dono: Lucas</span>
                </b-row>
                <b-row>
                    <b-button size="sm" class="mr-2" variant="info" to="/usuario/pets/consulta/1" >
                        Solicitar Consulta
                    </b-button>
                    <b-button size="sm" class="mr-2" variant="warning" to="/usuario/pets/editar/1" >
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
    }    
  },
  methods:{
    excluir(){
        console.log("Pet excluido");
    }
  }
}
</script>