<template>
  <div>
    <div class="container pt-5">
      <div class="mx-auto mt-5">
        <h1 class="text-center">PET Clinic</h1>
        <h2 class="text-center">Bem-Vindo! Faça login para continuar.</h2>
        <b-row class="mx-auto" align-h="center">
          <b-button variant="info" size="sm" class="mr-2" to="/loginUsuario">
            Área do usuário
          </b-button>
          <b-button variant="success" size="sm" class="mr-2" to="/loginVeterinario">
            Área do veterinário
          </b-button>
        </b-row>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
