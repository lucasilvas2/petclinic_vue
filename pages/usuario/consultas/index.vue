<template>
  <div>
    <div class="container pt-5">
      <div class="mx-auto mt-5">
        <h1 class="text-center">Consultas</h1>
        <b-table striped hover :items="pets" :fields="campos">
             
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
        'nome', 'estado', 'veterinario'
      ],
      pets:[
        {nome: 'Ventania', estado: 1, veterinario: 'João'},
        {nome: 'Bidu', estado: 0, veterinario: 'Pedro'},
        {nome: 'Totó', estado: 1, veterinario: 'Lucas'},
        {nome: 'Pingo', estado: 2,veterinario: 'Marcos'},                
      ]     
                
    }      
  }
}
</script>