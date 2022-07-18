<template>
  <div>
    <NavList />

    <div class="buttons">
      <a class="Cadastro">Cadastro</a>
      <a class="Listagem">Listagem</a>
      <button class="btn">Cadastrar Novo Usuario</button>
    </div>
    <div class="user">
      <br>
      <hr>
      <a id="cpf">CPF</a>
      <a id="FullName">Nome Completo</a>
      <hr>
    </div>
    <div id="renderResult">
      <br>
      <ul v-for="item in pageOfItems" :key="item.id">
    
          <li id="content-cpf" >{{ item.cpf | VMask(mask)}} <br></li>
        
          <br>
          <br>
          <li id="content-name" >{{ item.fullname }}  </li>
          <li><i @click="ModalOpen(item)" class="fa fa-eye" id="icon" aria-hidden="true"></i> </li>
      </ul>
      <ModalEye :User_Prop="User_Prop" v-show="openModal" />
    </div>
    <hr>
    <div class="card-footer pb-0 pt-3">
      <jw-pagination :disableDefaultStyles="true" value="Continuar" :labels="customLabels" :items="users"
        @changePage="onChangePage"></jw-pagination>
    </div>
    <br>
  </div>
</template>

<script>
import axios from 'axios'
import ModalEye from "@/components/ModalEye.vue";
import NavList from "../components/NavList.vue"

const customLabels = {
  first: '<<',
  last: '>>',
  previous: '<',
  next: '>'
};
export default {
  components: {
    NavList,
  ModalEye

  },
  data() {
    return {
      users: [{}],
      User_Prop: {} ,
      pageOfItems: [],
      customLabels,
      mask: "###.###.###.-##",
      openModal: false,
      
    };
  },
  created() {
    axios.get("/api/users/")
      .then((res) => this.users = res.data.users)
  },
  methods: {
    onChangePage(users) {
      this.pageOfItems = users;

    },
    ModalOpen(item) {
      this.User_Prop = item
      this.openModal = true
    },
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

.buttons {
  margin-top: 7%;
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
  margin: 16px 2px;
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

.pagination {
  cursor: pointer;
  position: static;
  margin-left: 23vw;
  list-style: none;
  display: inline-flex;
  width: 50vw;
  justify-content: space-between;
  font-size: 22px;
}

#renderResult {
  width: 64vw;
  margin-top: 28px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  margin-left: 15vw;
}
ul {
  display: flex;
  padding: 5px;
  align-items: center;
  justify-content: space-between;
}
ul li {
  font-size: 13px;
  list-style-type: none;
}

#content-name {
 margin-right: 15vw;
}
</style>  