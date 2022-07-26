<template>
  <div>
    <NavList />
    <br>
    <HeaderList />
    <div class="user">
      <br>
      <hr>
      <a id="cpf">CPF</a>
      <a id="FullName">Nome Completo</a>
      <hr>
    </div>
    <div id="renderResult">
      <br>
      <ul v-for="item in pageOfItems" :key="item.id" >

        <li id="content-cpf">{{ item.cpf | VMask(mask) }} <br></li>

        <br> 
        <br>
        <li id="content-name">{{ item.fullname }} </li>
        <li><i @click="ModalOpen(item)" class="fa fa-eye" id="icon" aria-hidden="true"></i> </li>
      </ul>
       
      <ModalEye :User_Prop="User_Prop" v-show="openModal" />
    </div>
    <ul v-for="(informacoes, index) in informacoes" :key="index">
          <li id="content-cpf"> {{informacoes.cpf}}</li>
            <li id="content-name">{{ informacoes.name }} </li>
        </ul>
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

const customLabels = {
  first: '<<',
  last: '>>',
  previous: '<',
  next: '>'
};
export default {
  components: {
    NavList,
    ModalEye,
    HeaderList

  },
  data() {
    return {
      users: [{}],
      User_Prop: {},
      pageOfItems: [],
      customLabels,
      mask: "###.###.###-##",
      openModal: false,
      informacoes:[],


    };
  },
  created() {
    axios.get("/api/users/")
      .then((res) => this.users = res.data.users)
       this.informacoes = (localStorage.getItem("informacoes")) ?  JSON.parse(localStorage.getItem("informacoes")) : [];
           
  },
  methods: {
    onChangePage(users) {
      this.pageOfItems = users;

    },
    ModalOpen(item) {
      this.User_Prop = item
      if(this.openModal == false){
      this.openModal = true
      }
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
 margin-right: 23vw;

}

</style>  