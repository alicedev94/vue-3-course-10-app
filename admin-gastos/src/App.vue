<script setup>
</script>

<template>
    <header>
          <h1>Planificador de Gastos</h1>
          <div class="contenedor-header contenedor sombra">
              <Presupuesto 
                  v-if="presupuesto === 0"
                  @definir-presupuesto="definirPresupuesto"
              />
              <ControlPresupuesto
                  v-else
                  :presupuesto="presupuesto"
                  :disponible="disponible"
                  :gastado="gastado"
                  @reset-app="resetApp"
              />
          </div>
      </header>

</template>

<style>
  :root {
    --azul: #3b82f6;
    --blanco: #FFF;
    --gris-claro: #F5F5F5;
    --gris: #94a3b8;
    --gris-oscuro: #64748b;
    --negro: #000;
  }
  html {
    font-size: 62.5%;
    box-sizing: border-box;
  }
  *,
  *:before,
  *:after {
    box-sizing: inherit;
  }
  body {
    font-size: 1.6rem;
    font-family: "Lato", sans-serif;
    background-color: var(--gris-claro);
  }
  h1 {
    font-size: 4rem;
  }
  h2 {
    font-size: 3rem;
  }
  header {
    background-color: var(--azul);
  }
  header h1 {
    padding: 3rem 0;
    margin: 0;
    color: var(--blanco);
    text-align: center;
  }
  /* .fijar {
    overflow: hidden;
    height: 100vh;
  }
  header {
    background-color: var(--azul);
  }
  header h1 {
    padding: 3rem 0;
    margin: 0;
    color: var(--blanco);
    text-align: center;
  }
  .contenedor { 
      width: 90%;
      max-width: 80rem;
      margin: 0 auto;
  }
  .contenedor-header {
    margin-top: -5rem;
    transform: translateY(5rem);
    padding: 5rem;
  }
  .sombra {
    box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
    background-color: var(--blanco);
    border-radius: 1.2rem;
    padding: 5rem;
  }
  
  .crear-gasto {
    position: fixed;
    bottom: 5rem;
    right: 5rem;
  }
  .crear-gasto img {
    width: 5rem;
    cursor:pointer;
  }
  .listado-gastos {
    margin-top: 10rem;
  }
  .listado-gastos h2 {
      font-weight: 900;
      color: var(--gris-oscuro);
  } */

</style>

