<template>
    <div class="modal" id="myModal" v-show="modal">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-body">


                    <div id="#botoes">
                        <button id="dados" class="active">Dados</button>
                    </div>
                    <br>
                    <div id="border">
                        <h2 id="title">Dados de Contato</h2>
                        <br>
                        <div>
                            <br>
                            <p id="nome">Nome: </p>
                           <br />
                            <p id="email">Email:</p>
                            <br>
                            <p id="cpf">CPF:</p>
                            <p id="UserCpf"></p>
                            <br>
                            <p id="telefone">Telefone:</p>
                            <br>
                        </div>
                    </div>
                </div>
                <div class="modal-footer">
                    <button v-on:click="close" type="button" class="btn-danger" data-dismiss="modal">Cancelar</button>
                    <button class="btn">Continuar</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            modal: true,
            users: [{}],
        };
    },
    created() {
        this.users = axios.get("/api/users/")
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
        close: function () {
            if (this.modal) {
                this.modal = false
            }
        },
    },
}
</script>

<style scoped>
#title {
    margin-top: 12px;
    margin-left: 37px;
    border-bottom: solid 2px grey;
    margin-right: 55px;
}

.modal {
    background-color: rgba(0, 0, 0, .8);
    position: fixed;
    display: table-column-group;
    top: 0px;
    left: 0;
    width: 100vw;
    height: 100vh;
}

.modal-content {
    margin: 0 auto;
    margin-top: 1%;
    max-width: 600px;
    background-color: #eee;
    padding: 43px 34px;
    box-shadow: 0 0 2px #fff;
    border-radius: 25px
}

.modal-body {
    padding: 64px;
    height: 500px;
}

.btn-danger {
    font-size: 20px;
    padding: 11px 55px;
    border: 0px;
    border-radius: 3px;
    color: white;
    background-color: rgb(12, 12, 12);
    cursor: pointer;
    margin-left: 38px;
    margin-top: -7px;
}

.btn-danger:hover {
    background-color: rgb(117, 111, 111);
}

.btn {
    font-size: 20px;
    padding: 11px 55px;
    border: 0px;
    border-radius: 3px;
    color: white;
    background-color: rgb(255, 20, 106);
    cursor: pointer;
    border-bottom: solid 2px #ff0054;
    margin-left: 10px;
    margin-top: 62px;
}

.btn:hover {
    background-color: rgba(255, 20, 106, 0.616);
}

#dados {
    font-size: 20px;
    padding: 8px 39px;
    border: solid 2px black;
    border-radius: 23px;
    color: white;
    margin-left: 10px;
    background-color: black;
}

#nome {
    margin-left: 9%;
    margin-top: 4%;
    font-size: 19px;
}

#email {
    margin-left: 9%;
    margin-top: 4%;
    font-size: 19px;
}

#cpf {
    margin-left: 9%;
    margin-top: 4%;
    font-size: 19px;
}

#telefone {
    margin-left: 9%;
    margin-top: 4%;
    font-size: 19px;
}
</style>