<template>
  <section class="information-modal" v-show="modal">
    <span v-on:click="close" class="close">X</span>
    <nav class="navbar-modal">
      <h4>Detalhes do usuário</h4>

    </nav>

    <div class="contain-all-information">
      <div class="informations">
        <div class="information-content">
          <label>Cpf</label>
          <span>{{ User_Prop.cpf }}</span>
          <span></span>
        </div>
        <div class="information-content">
          <label>Nome completo</label>
          <span>{{ User_Prop.fullname }}</span>
        </div>
        <div class="information-content">
          <label>Nascimento</label>
          <span>{{ User_Prop.birthDate }}</span>
        </div>
      </div>

      <div class="informations">
        <div class="information-content">
          <label>Celular</label>
          <span>{{ User_Prop.phone }}</span>
        </div>
        <div class="information-content">
          <label>Contato</label>
          <span>
            <p>Whatsapp</p>
          </span>
        </div>
        <div class="information-content">
          <label>Email</label>
          <span class="modal-email">{{ User_Prop.email}}</span>
        </div>
      </div>
    </div>
  </section>
</template>


<script>

export default {
  props: {
    User_Prop: {
      type: Object
    }
  },

  data() {
    return {
      modal: true
    };
  },
  methods: {
    close: function () {
      if (this.modal == true) {
        this.modal = false
      }
    },
    log() {
      console.log(this.User_Prop)
    }
  },
}
</script>
</script>

<style scoped>
.information-modal {
  width: 450px;
  height: auto;
  flex-direction: column;
  border-radius: 10px;
  background-color: white;
  position: absolute;
  top: 45%;
  left: 50%;
  right: -50%;
  transform: translate(-50%, -50%);
  box-shadow: 0px 0px 1px 1100px rgba(0, 0, 0, 0.239);
}

.navbar-modal {
  width: 100%;
  height: 45px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.contain-all-information {
  margin: 20px;
  margin-top: 10px;
  padding: 40px;
  display: flex;
  justify-content: space-between;
  border: 2px solid rgba(211, 211, 211, 0.542);
  border-style: dashed;
}

.informations {
  width: 45%;
}

.information-content {
  margin: 15px 0px;
  display: flex;
  flex-direction: column;
}

.close {
  position: absolute;
  right: 20px;
  border: none;
  background-color: transparent;
}

.close:hover {
  cursor: pointer;
  transform: translateZ(0px) scale(1.2);
}

.close {
  width: 21px;
  height: 21px;
  color: rgb(75, 75, 75);
}

span {
  font-weight: bold;
  display: flex;
  align-items: center;
}

label {
  font-size: 14px;
}

.modal-email {
  font-size: 13px;
}
</style> 