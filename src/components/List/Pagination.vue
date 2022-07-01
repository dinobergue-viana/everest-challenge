<template>
    <div class="card text-center m-3">
        <div class="card-body">
            <div v-for="user in pageOfItems" :key="user.id">{{user.fullname}}</div>
        </div>
        <div class="card-footer pb-0 pt-3">
            <jw-pagination :items="pageOfItems" @changePage="onChangePage"></jw-pagination>
        </div>
    </div>
</template>

<script>
// an example array of items to be paged
const exampleItems = [...Array(1).keys()].map(i => ({ id: (i+1), name: 'Item ' + (i+1) }));
import axios from 'axios'
export default {
    data() {
        return {
            exampleItems,
            
            pageOfItems:[
              { fullname: '...', cpf: 'Carregando' },
              { fullname: '...', cpf: 'Carregando' },
              { fullname: '...', cpf: 'Carregando' },
              ],   
        mask: 'AAAAAAAAAA',
        };
    },
    created() {
      axios.get("/api/users")
        .then((res) => this.users = res.data)
        .then((json) => {
          this.Users = json.users
          this.mask = '###.###.###-##'
          console.log(this.exampleItems)
      })  
    },
    methods: {
        onChangePage(pageOfItems) {
            // update page of items
            this.pageOfItems = pageOfItems;
        }
    }
};
</script>



<!-- <template>
<div>
    <button class="newUser">Cadastrar novo usuário</button> 
  <div class="main_box">
    <div class="list_box">
      <ul>
        <h3>CPF</h3>
        <li class="cpf" v-for="user in users" :key="user.id">{{user.cpf | VMask(mask)}}</li>
        
      </ul>
      <ul id="users">
        <h3>NOME COMPLETO</h3>
        <li class="name" v-for="user in users" :key="user.id">
          {{user.fullname}}
          <f-icon icon="fa-solid fa-eye"  class="eye"/>
        </li>
      </ul>
      
    </div>
    <div class="card-footer pb-0 pt-3">
      <jw-pagination :items="users" @changePage="onChangePage"></jw-pagination>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios"
export default {
    data() {
      return {
        users:[
              ({ fullname: '...', cpf: 'Carregando' }),
              ({ fullname: '...', cpf: 'Carregando' }),
              ({ fullname: '...', cpf: 'Carregando' }),
              ],   
        mask: 'AAAAAAAAAA',
        
        
        
      }
    },

    created() {
      axios.get("/api/users")
        .then((res) => this.users = res.data)
        .then((json) => {
          this.users = json.users
          this.mask = '###.###.###-##'
      })  
    }
  }


</script>

<style>
    h3{
    border-top: solid 1px rgb(223, 219, 219);
    border-bottom: solid 1px rgb(223, 219, 219);
    margin-bottom:3vw;
    padding: 0.5vw 0 0.5vw 0;
  }

  li{
    margin: 1vw 0 1vw 0;
    font-weight: 100;
  }
  .content{
    padding-left: 2em;
    margin-left: 27%;
    width: 45.2vw;

  }

  .eye:hover
    {
    animation:eye-pop 0.1s linear both
    } 
    @keyframes eye-pop
    {
    0%{box-shadow:0 0 #3e3e3e,0 0 #3e3e3e,0 0 #3e3e3e,0 0 #3e3e3e,0 0 #3e3e3e,0 0 #3e3e3e,0 0 #3e3e3e,0 0 #3e3e3e;
      transform:translateX(0) translateY(0)}
     100%{box-shadow:0.5px -0.5px #3e3e3e,2px -2px #3e3e3e,3px -3px #3e3e3e,4px -4px #3e3e3e,5px -5px ;
     transform:translateX(-1px) translateY(1px)}
    }

  .newUser:hover{
    background-color: rgb(255, 255, 255);
    border: solid 1px rgb(255, 26, 95);
    color: rgb(255, 26, 95)
  }
  
  .newUser{
    width:12em;
    height:3em;
    font-size:1vw;
    float: right;
    background-color: rgb(255, 26, 95);
    border: none;
    border-radius: 12px;
    margin:2vw;
    color:white;
  }


  .main_box{
    width: 42.2vw;
    padding: 0.5vw ;
    display:flex;
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
    width: 15em;
    font-size: 20px;
  }

  .name{
    display: flex;
    justify-content: space-between;
    list-style: none;
    width: 30em;
    font-size: 20px;

  }
</style>-->