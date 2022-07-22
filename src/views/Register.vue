<template>
  <div class="form-container">
    <NavList />
    <br>
    <HeaderList />
    <hr>
    <br>
    <div id="centralBox">
      <form id="form1">

        <div id="texts">

          <h2 class="title">Dados de contato</h2>
          <br />
          <p class="text">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Orci,
            volutpat in <br />iaculis nec nisl tellus.
          </p>
          <br />
        </div>
        <label>Nome completo</label>
        <br />
        <input type="text" v-model="form.name" placeholder='Seu nome' class="bigInput" />
        <div id="labelEmail">
          <label>E-mail</label>
          <label id="cidade">Confirmar o Email</label>
        </div>
        <div>
          <div id="email">

            <input v-model="form.email" placeholder="Seu_Email@email.com" type="text" class="mediumInput" />


            <input type="text" v-model="form.confirmEmail" placeholder="confirme seu email" class="mediumInput paddingInput" />

          </div>
        </div>
        <div id="labelNumbers">
          <label>Cpf</label>
          <label>Celular</label>
        </div>
        <div id="numbers">
          <input v-model="form.cpf" maxlength="14" placeholder='000.000.000-00' type="text" class="mediumInput" />
          <input placeholder="(00) 111111-22222" type="text" v-model="form.telefone" autocomplete="off" maxlength="15"
            minlength="14" class="mediumInput paddingInput" />
        </div>
        <label>Data de nascimento</label>
        <br />
        <input v-model="form.date" type="date" class="mediumInput" />
        <p class="bottonText">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit
        </p>
        <br />
        <p class="bottonText">Mattis semper odio preretium vestibulum nulla</p>
        <br />
        <div id="sms">
          <input type="checkbox" />
          <label>Email e SMS</label>
        </div>
        <div id="mensageApp">
          <input type="checkbox" />
          <label>Whatsapp</label>
          <br>
          <hr>
        </div>
        <div class="btns">
          <hr>
          <br>
          <button type="submit" id="concluir" @click="userCreate(form)"> Salvar </button>

          <button id="cancelar">Cancelar</button>
        </div>
      </form>

    </div>
  </div>
</template>

<script>
import NavList from "../components/NavList.vue"
import HeaderList from "../components/HeaderList.vue"
import axios from 'axios'

export default {
  components: {
    NavList,
    HeaderList,
  },
  data() {
    return {
      form: {
        name: "",
        email: "",
        confirmEmail: "",
        telefone: "",
        date: "",
        cpf: ""
      },

    }

  },
  methods: {
    
    async userCreate(form) {
      try {
           const newUser = {fullname:form.name, email:form.email, confirmEmail:form.confirmEmail, telefone:form.telefone, date:form.date,cpf:form.cpf} 
           const response = await axios.post ("/api/users", newUser)
          this.$router.push("/")
}
         catch (error){
            console.log(error);
       }
  
    }
  
    
  },

}
</script>

<style scoped>
* {
  color: black;
}

input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

input[type="number"] {
  -moz-appearance: textfield;
  appearance: textfield;
}

hr {
  margin-left: 13%;
  margin-right: 18%;
}

#contents {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 84px;
}

#centralBox {
  height: 800px;
  width: 1161px;
  display: flex;
  flex-direction: column;

}

#form1 {
  z-index: 0;
  right: -450;
  margin-left: 21vw;
}

input {
  margin-bottom: 20px;
  margin-top: 0px;
}

.title {
  border-left: solid 6px rgb(255, 0, 85);
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  color: black;
  font-size: 39px;
}

.bigInput {
  height: 40px;
  width: 828px;
  border-radius: 5px;
  font-size: 20px;
  border: solid 2px black;
}

.mediumInput {
  height: 40px;
  width: 387px;
  border-radius: 5px;
  font-size: 20px;
  border: solid 2px black;
  display: flex;
  flex-direction: row-reverse;
}

#labelEmail {
  display: flex;
  justify-content: space-between;
  width: 494px;
}

#labelNumbers {
  display: flex;
  justify-content: space-between;
  width: 494px;
}

#email {
  display: flex;
  justify-content: flex-start;
}

#numbers {
  display: flex;
  justify-content: flex-start;
}

#logradouro2 {
  display: flex;
  justify-content: flex-start;
}

.paddingInput {
  margin-left: 56px;
}

#sms {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  width: 120px;
}

#mensageApp {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  width: 100px;
}

#concluir {
  font-size: 20px;
  padding: 11px 55px;
  border: 0px;
  border-radius: 3px;
  color: white;
  background-color: rgb(255, 20, 106);
  cursor: pointer;
  border-bottom: solid 2px #ff0054;
  margin-left: 20vw;
}

#concluir:hover {
  background-color: rgba(255, 20, 106, 0.616);
}

#cancelar {
  font-size: 20px;
  padding: 11px 55px;
  border: 0px;
  border-radius: 3px;
  color: rgb(0, 0, 0);
  background-color: rgb(248, 248, 248);
  cursor: pointer;
  margin-left: 10px;
}

#cancelar:hover {
  background-color: rgba(164, 164, 164, 0.616);
}
</style>