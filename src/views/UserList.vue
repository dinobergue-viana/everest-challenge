<template>
  <div>
    <NavList />
    <br>
    <br>
    <br>
    <br>
    <br>
    <div>
      <a class="Cadastro">Cadastro</a>
      <a class="Listagem">Listagem</a>
      <br>
      <br>
      <br>
      <br>
      <button class="btn">Cadastrar Novo Usuario</button>
    </div>
    <div class="user">
      <br>
      <br>
      <hr>
      <a id="cpf">CPF</a>
      <a id="FullName">Nome Completo</a>
      <br>
      <br>
      <hr>
    </div>
    <div>
      <br>
      <div id="pagination">
        <Pagination />
        <br>
        <br>
      </div>
    </div>
  </div>

</template>

<script>
import NavList from "../components/NavList.vue"
import axios from 'axios'
import Pagination from '../components/Pagination.vue'
export default {
  components: {
    NavList,
    Pagination,
  
  },

};
</script>

<style scoped>
.Cadastro {
  color: #000000;
  font-size: 19px;
  margin-left: 43%;
  border-bottom: 3px solid rgb(22, 21, 21);
  transition-duration: 0.3s;
  cursor: pointer;
}

.Cadastro:hover {
  color: rgb(140, 130, 130);
  border-bottom: 3px solid rgb(140, 130, 130);
}

.Listagem {
  color: rgb(140, 130, 130);
  border-bottom: 3px solid rgb(140, 130, 130);
  font-size: 19px;
  margin-left: 5%;
}

.btn {
  border: solid 2px rgb(255, 35, 123);
  background-color: white;
  color: rgb(0, 0, 0);
  padding: 16px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
  border-radius: 11px;
  margin-left: 60%;
}

.btn:hover {
  background-color: rgb(255, 35, 123);
  color: white;
}

hr {
  margin-left: 13%;
  margin-right: 18%;
}

#cpf {
  margin-left: 19%;
}

#FullName {
  margin-left: 294px;
}

.user {
  display: inline;
}
</style>