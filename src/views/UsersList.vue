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
      <br>
      <hr>
    </div>
    <div>
      <br>
      <UsersList />
      <br>
      <br>
      <hr>
      </div>
    </div>
</template>

<script>
import NavList from "../components/NavList.vue"
import UsersList from '../components/UsersList.vue'
import axios from 'axios'
export default {  
  components: {
    NavList,
    UsersList,

},

};
</script>

<style scoped>
.Cadastro {
  color: #000000;
  font-size: 19px;
  margin-left: 50%;
  border-bottom: 3px solid rgb(22, 21, 21);
  cursor: pointer;
}

.Cadastro:hover {
  color: rgb(140, 130, 130);
  border-bottom: 3px solid rgb(140, 130, 130);
}

.Listagem {
  color: #000000;
  font-size: 19px;
  margin-left: 5%;
  border-bottom: 3px solid rgb(22, 21, 21);
  cursor: pointer;
}

.Listagem:hover {
  color: rgb(140, 130, 130);
  border-bottom: 3px solid rgb(140, 130, 130);
}

.btn {
  text-align: center;
  margin-left: 57%;
  height: 56px;
  padding: 15px 32px;
  text-align: center;
  display: inline-block;
  font-size: 26px;
  color: #060606;
  border-radius: 14px;
  border: solid 2px rgb(255, 35, 123);
  background-color: rgb(255, 35, 123);
  text-align: center;
  cursor: pointer;
}

.btn:hover {
  background-color: white;
  border: solid 2px rgb(255, 35, 123);
}

hr {
  margin-left: 13%;
  margin-right: 18%;
}

#cpf {
  margin-left: 19%;
}

#FullName {
  margin-left: 15%;
}

.user {
  display: inline;
}
</style>