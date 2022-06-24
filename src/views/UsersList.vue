<template>
  <div id="userList">
    <div class="container">
      <div id="header">
        <p class="headerCpf margin">CPF</p>
        <p class="headerNome margin">NOME COMPLETO</p>
      </div>
      <div id="cpf">
        <p class="Cpf margin">104.339.039.10</p>
      </div>
      <div id="nome">
        <p class="Nome margin">Lucas Gabriel Devigili</p>
      </div>
      <div id="hidden">
        <i class="fa-solid fa-eye click"></i>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "UsersList",
};
</script>

<style scoped>
#userList {
  height: 60ch;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.container {
  /* background-color: aqua; */
  height: 57ch;
  width: 60vw;
  border-bottom: 1px solid rgb(189, 189, 189);
  display: grid;
  grid-template-columns: 30fr 70fr 10fr;
  grid-template-rows: 5vh 5vh;
  grid-template-areas:
    "header header header"
    "cpf nome hiden";
}

#header {
  /* background-color: bisque; */
  font-weight: 700;
  grid-area: header;
  border-top: 1px solid rgb(189, 189, 189);
  border-bottom: 1px solid rgb(189, 189, 189);
  display: grid;
  align-items: center;
  grid-template-columns: 30fr 80fr;
}

#cpf {
  /* background-color: blueviolet; */
  grid-area: cpf;
  display: flex;
  align-items: center;
}

#nome {
  /* background-color: chartreuse; */
  grid-area: nome;
  display: flex;
  align-items: center;
}

.margin {
  margin-left: 20px;
}

#hidden {
  /* background-color: brown; */
  grid-area: hiden;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
