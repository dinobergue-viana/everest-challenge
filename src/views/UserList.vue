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
    <div class="card text-center m-3">
      <br>
      <div id="usuarios">
        <div>
          <p id="UserCpf" v-for="item in pageOfItems" v-mask="'###.###.###-##'" :key="item.id">{{ item.cpf | VMask(mask)
          }} <br></p>
        </div>
        <div id="nome">
          <br>
          <br>
          <p id="UserName" v-for="item in pageOfItems" :key="item.id">{{ item.fullname }} <br> <i @click="ModalOpen" class="fa fa-eye"
              id="icon" aria-hidden="true"></i> </p>
        </div>
      </div>
      <ModalEye v-show="openModal" />
      <br>
      <br>
      <hr>

    </div>
    <div class="card-footer pb-0 pt-3">
      <jw-pagination :disableDefaultStyles="true" value="Continuar"  :labels="customLabels"
        :items="users" @changePage="onChangePage"></jw-pagination>
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
      pageOfItems: [],
      customLabels,
      mask: "###.###.###.-##",
      openModal: false
    };
  },
  created() {
       axios.get("/api/users/")
      .then((res) => this.users = res.data)
      .then((json) => {
        this.users = json.users
      })
  },
  methods: {
    onChangePage(users) {
      this.pageOfItems = users;
      console.log(users);
    },
      ModalOpen(){
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
.buttons{
  margin-top:7% ;
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

#usuarios {
  display: inline-flex;
  margin-top: -84px;
  margin-left: 23%;
  justify-content: center;
  align-items: flex-end;
}

#UserCpf {
  margin-left: 17%;
  margin-top: 35%;
}

#UserName {
  margin-left: -258%;
  margin-top: 15%;
  padding-left: 108%;
  display: block;
  height: 47px;
}

#nome {
  margin-left: 107%;
  margin-top: -7%;
  padding-left: 8%;
}

hr {
  margin-left: 13%;
  margin-right: 18%;
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


#icon {
  margin-left: 308%;
}
</style>  