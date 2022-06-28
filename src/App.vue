<template>
  <div id="app">
    <div class="view-container">
      <router-view/>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Navbar from "./components/NavList.vue"

export default {
  name: 'App',
  data() {
    return {
      headerTitle: "Usuários"
    }
  },
  components: {
    Header,
    Navbar
  }
}
</script>

<style>
/* SINTA-SE A VONTADE PARA ALTERAR ESSAS ESTILIZAÇÕES BASICAS */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}
</style>
