<template>
  <div >
    <NavList />
    <br>
    <HeaderList/>
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

          <li id="content-name" >{{ item.fullname }}  </li>
          <li><i @click="ModalOpen(item)" class="fa fa-eye" id="icon" aria-hidden="true"></i> </li>
      </ul>
      <ModalEye :userProp="userProp" v-show="openModal" />
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
import HeaderList from "../components/HeaderList.vue"


export default {
  components: {
  NavList,
  ModalEye,
  HeaderList

  },
  data() {
    return {
      users: [{}],
      userProp: {} ,
      pageOfItems: [],
      customLabels,
      mask: "###.###.###.-##",
      openModal: false,
      
    };
    
  },
  created() {
      try {
      const response = axios.get("/api/users/")
      this.users = response.data.users
    } catch(error) {
      Alert(`Ocorreu um erro ao buscar usuários: ${error.message}`)
    }
  },
  methods: {
    onChangePage(users) {
      this.pageOfItems = users;

    },
    ModalOpen(item) {
      this.userProp = item
      this.openModal = true
    },
  },  
};
</script>
<style scoped>
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
 font-size: 19px;
  list-style-type: none;
}

#content-name {
 margin-right: 19vw;

}
</style>  