<template>
<div class="content">
  <button class="newUser">Cadastrar novo usuário</button>
  <div class="main_box">
    <div class="list_box">
      <ul>
        <h3>CPF</h3>
        <li class="cpf" v-for="user in users" :key="user.id">{{user.cpf | VMask('###.###.###-##')}}</li>
      </ul>
      <ul id="users">
        <h3>NOME COMPLETO</h3>
        <li class="name" v-for="user in users" :key="user.id">{{user.fullname}}</li>
      </ul>
      <span>{{ '9999999999'  }}</span>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios"
  export default {
    name: "app",
  
    data() {
      return {
        users:[
              ({ fullname: '...', cpf: 'Carregando' }),
              ({ fullname: '...', cpf: 'Carregando' }),
              ({ fullname: '...', cpf: 'Carregando' }),
                
              ],
        mask: ['(', /\d/, /\d/, /\d/, ') ', /\d/, /\d/, /\d/, '-', /\d/, /\d/, /\d/, /\d/],
                
      }
    },

    created() {
      axios.get("/api/users")
        .then((res) => this.users = res.data)
        .then((json) => {
          this.users = json.users
      })  
    }
  }

</script>

<style scoped>
  h3{
    border-top: solid 1px rgb(223, 219, 219);
    border-bottom: solid 1px rgb(223, 219, 219);
    margin-bottom:3vw;
    padding: 0.5vw 0 0.5vw 0;
  }
  .content{
    padding-left: 2em;
    margin-left: 27%;
    width: 45.2vw;

  }
  
  .newUser{
    width:10vw;
    height:2vw;
    float: right;
    background-color: rgb(255, 26, 95);
    border: none;
    border-radius: 12px;
    margin:1vw;
    color:white;
  }
  .main_box{
    width: 42.2vw;
    padding: 0.5vw ;
    display:flex;
    background-color: rgba(0, 255, 255, 0.445);
    justify-content: space-evenly;
  }

  .list_box{
    border-bottom: solid 1px rgb(223, 219, 219);
    display: grid;
    padding-bottom:1vw ;
    grid-template-columns: auto auto;
  }

  .cpf{
    list-style: none;
    width: 10em;
    font-size: 20px;
  }

  .name{
    list-style: none;
    width: 30em;
    font-size: 20px;

  }

</style>