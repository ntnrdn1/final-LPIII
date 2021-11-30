<template>
  <div id="container">
    <div>
      <p>O que você deseja fazer?</p>
      <a href="/tabs/galeria">Acessar minha galeria</a>
      </div>
      <div>
      <a href="/tabs/consulta">Consultar localização</a>
        </div>
  </div>
</template>

<script lang="ts">

export default {
  name: 'ExploreContainer',
  props: {
    name: String
  }
}
</script>

<style scoped>

#container {
        font-family: Avenir, Helvetica, Arial, sans-serif;
    background: #FFF;
    color: #364253;
    height: 100%;
    display: grid;
    grid-template-rows: auto;
    justify-content: center;
    align-content: center;
}


#container p {
  text-decoration: none;
    color: #364253;
    align-items: center;
    align-content: center;
  
    justify-items: center;
    
    font-size: 1.3rem;
    text-align: center;
  
}

a {
    text-decoration: none;
    padding: 0.5rem 1rem;
    color: #fff;
    border-radius: 5rem;
    margin-top: 20%;
    box-shadow: 2px 8px 11px rgba(0, 0, 0, 0.2);
    border: none;
    width: max-content;
    font-size: 1.3rem;
    background: linear-gradient(to right, #4091dd, #28b4d2);
    font-weight: 100;
    outline: none;
    cursor: pointer;
        display: grid;
    grid-template-columns: 1fr;
    grid-auto-rows: auto;
    grid-gap: 2rem;
    justify-items: center;
  }


</style>