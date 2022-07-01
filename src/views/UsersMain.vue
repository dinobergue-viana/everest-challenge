<template>
<div class="content">
  <ListSwich @changeCad="change" @changeList="change" />
  <UserCad v-show="swich==false"/>
  <Pagination v-show="swich==true"/>
</div>
</template>

<script>

import Pagination from "@/components/List/Pagination.vue"
import ListSwich from "../components/List/UsersList.vue"
import UserCad from "@/components/List/UserCad.vue"
  export default {
    
    name: "app",
    components:{
      ListSwich,
      Pagination,
      UserCad
    },
    
    methods: {
      change(value){
        this.swich = value
      }
    },
    data() {
      return {        
        swich:true
      }
    },

    
  }

</script>

<style scoped>
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

</style>