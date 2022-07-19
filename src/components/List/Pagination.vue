<template>
<div class="box">
<NewButtom @click.native="a"/>
  <div v-show="hasUsers" class="list_box">
    <ul>
      <h3>CPF</h3>
      <div class="itens_box">
        <li class="list" v-for="user in pageOfItems" :key="user.id">
          {{user.cpf | VMask(mask)}}
        </li>
      </div>
    </ul>
      
    <ul>
      <h3>Nome Completo</h3>
      <div class="itens_box">
        <li class="namesList" v-for="user in pageOfItems" :key="user.id">
          <span class="fullname">{{user.fullname}}</span>
          <f-icon @click="DatailUser(user)" icon="fa-solid fa-eye"  class="eye"/>
        </li>
      </div>
    </ul>
  </div>
  <div v-show="!hasUsers" class="noUser">
    <NothingHere />
    <h1 class="noUserMsg">Nada por aqui</h1>
  </div>
  <div class="pagBox">
    <jw-pagination :maxPages="3" :pageSize="limit" :labels="MenuLabels"  :items="Users" @changePage="onChangePage"></jw-pagination>
  </div>
</div>
</template>

<script>

const MenuLabels = {
    first: '<<',
    last: '>>',
    previous: '<',
    next: '>'
};

import axios from 'axios'
import ValidateTest from "../../utils/validateCPF.ts"
import NewButtom from '@/components/List/NewButtom.vue'
import NothingHere from "../NothingHere.vue"
export default {
    data() {
        return {
            pageOfItems:[],
            Users:[],   
            mask: 'AAAAAAAAAA',
            limit:6,
            MenuLabels,
            hasUsers:true,
            ValidateTest,
        };
    },
    components:{
      NewButtom,
      NothingHere
    },

    
    created() {
      axios.get("/api/users")
        .then((res) => this.users = res.data)
        .then((json) => {
          this.Users = json.users
          this.mask = '###.###.###-##'
      if(this.Users.length == 0){
        this.hasUsers = false
        this.ValidateTest.validate("nada por aqui")
      }
      })  
    },
    methods: {
      a(){
        alert('AAA')
      },
        onChangePage(User) {
            this.pageOfItems = User;

        },

        DatailUser(info){
          this.$emit("SendUser",info)
        }
    }
};
</script>
<style scoped>
  .box{
    position: absolute;
    animation-name: boxIn;
    animation-duration: 0.5s;
    animation-fill-mode: forwards;
    max-width:45%;
    min-width: 10%;
    margin-top:-4vw ;
  }

  @keyframes boxIn{
    from{margin:20vw; opacity: 0%;}
    to{margin:10vw 0vw 0vw 0vw;opacity: 100%;}
  }
  li{
    margin: 1vw 0 1vw 0;
    font-weight: 100;
    list-style: none;
    font-size:110%
  }

  h3{
    border-top: solid 1px rgb(223, 219, 219);
    border-bottom: solid 1px rgb(223, 219, 219);
    padding: 1vw 0 1vw 2vw;
  }

  .list_box{
    width: 42.2vw;
    padding: 0.5vw;
    display:grid;
    grid-template-columns: 40% 60%;
    margin-top: min(20%, 50vw);
  }
  
  .namesList{
    display:flex;
    justify-content: space-between;
  }

  .fullname{
    text-overflow: ellipsis;
    overflow: hidden;

    width: 20vw;
    
    white-space: nowrap;
  
  
  
  /* padding: 20px;
  font-size: 1.3rem;
  margin: 0;
  background: white; */
 
  }

  .itens_box{
    margin-left:2vw
  }

  .eye:hover{
    color:rgb(255, 0, 76);
    transform: translateZ(10px) scale(1.5);
  }

  .pagBox{
    width: 100.2%;
    text-align: center;
    margin-top:1vw;
  }

  .noUser{
    margin-top:5vw;
    width:37vw;
    display: flex;
    justify-content: center;
  }

  .noUserMsg{
    position: absolute;
    width:37vw;
    height: 17vh;
    text-align: center;
    margin-top:10vh;
    padding-top:4vh;
    color:white;
    margin-left: 3vw;
    background-color: rgba(0, 0, 0, 0.757);
  }

@media (max-width:600px){

  


}
</style>

