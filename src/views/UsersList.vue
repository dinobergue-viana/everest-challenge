<template>
  <div id="userList">
    <div class="container">
      <div id="header">
        <p class="headerCpf margin">CPF</p>
        <p class="headerNome margin">NOME COMPLETO</p>
      </div>
      <div id="cpf">
        <p id="UserCpf" class="Cpf margin" v-for="i in users" :key="i.id ">{{i.cpf}}</p>
      </div>
      <div id="nome">
        <p id="UserName" class="Nome margin" v-for="i in users" :key="i.id">
          <br />{{ i.fullname }} <br />
        </p>
      </div>
      <div id="hidden">
        <i class="fa-solid fa-eye click"></i>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "UsersList",
  data() {
    return {
      users: [{}],
    };
  },
  created() {
    this.users = axios
      .get("/api/users/")
      .then((res) => (this.users = res.data))
      .then((json) => {
        this.users = json.users;
      });
  },
};
</script>

<style scoped>
#userList {
  height: 60ch;
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.container {
  height: 57ch;
  width: 60vw;
  border-bottom: 1px solid rgb(189, 189, 189);
  display: grid;
  grid-template-columns: 30fr 70fr 10fr;
  grid-template-rows: 5vh 5vh;
  grid-template-areas:
    "header header header"
    "cpf nome hiden";
}

#header {
  font-weight: 700;
  grid-area: header;
  border-top: 1px solid rgb(189, 189, 189);
  border-bottom: 1px solid rgb(189, 189, 189);
  display: grid;
  align-items: center;
  grid-template-columns: 30fr 80fr;
}

#cpf {
  grid-area: cpf;
  display: flex;
  align-items: center;
}

#nome {
  grid-area: nome;
  display: flex;
  align-items: center;
}

.margin {
  margin-left: 20px;
}

#hidden {
  grid-area: hiden;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
