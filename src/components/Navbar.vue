<template>
  <header>
    <div id="btnNav">
      <input type="button" value="Cadastro" class="btnNav click">
      <input type="button" value="Listagem" class="btnNav click">
    </div>
    <div id="btnCadastro">
      <input type="button" value="Cadastrar novo usuário" class="btnCadastro click">
    </div>
  </header>
</template>

<script>
export default {
  name: 'NavBar'
}
</script>

<style scoped>
header {
  height: 25ch;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: center;
}

.btnNav {
 height: 74px;
 width: 140px;
 font-size: 17px;
 background-color: transparent;
 border: transparent;
}

#btnCadastro {
  width: 40vw;
  display: flex;
  justify-content: end;
}

.btnCadastro {
    height: 60px;
    width: 220px;
    font-size: 16px;
    color: white;
    background-color: rgb(224, 43, 87);
    border: transparent;
    border-radius: 10px;
}

.btnCadastro:hover {
  background-color: rgb(199 18 62);
}
</style>