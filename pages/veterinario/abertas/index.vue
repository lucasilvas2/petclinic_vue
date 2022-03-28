<template>
  <div>
    <HeaderUsuario/>
    <div class="container pt-5">
      <div class="mx-auto mt-5">
        <h1 class="text-center">Consultas Abertas</h1>

        <b-table striped hover :items="consultas" :fields="campos">
            <template #cell(Ações)="row">
                <b-button size="sm" class="mr-2" @click="aceitar"> 
                    Aceitar
                </b-button>
                <b-button size="sm" class="mr-2" @click="recusar"> 
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
  name: 'Consultas_abertas',
  data(){
    return{
      campos:[
        'nome', 'data', 'veterinario','Ações'
      ],
      consultas:[
        {nome: 'Ventania', data: '20-05-2022', veterinario: 'João'},
        {nome: 'Bidu', data: '20-05-2022', veterinario: 'Pedro'},
        {nome: 'Totó', data: '20-05-2022', veterinario: 'Lucas'},
        {nome: 'Pingo', data: '20-05-2022', veterinario: 'Marcos'},                             
      ]     
                
    }      
  }
}
</script>
