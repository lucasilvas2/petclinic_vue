<template>
  <div>
    <b-navbar type="ligth" variant="dark">
      <b-collapse id="nav-collapse" is-nav >
        <b-navbar-nav >
          <b-nav-item to="/veterinario/abertas">Consultas Abertas</b-nav-item>
          <b-nav-item to="/veterinario/aceitas">Consultas Aceitas</b-nav-item>
          <b-nav-item to="/veterinario/rejeitadas">Consultas Rejeitadas</b-nav-item>
        </b-navbar-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-item to="/">Sair</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>  
  </div>
</template>