<template>
<div class="all">
    <div class="modal-shadow" @click="byeModal()">
    </div>
    <div class="modal-content" >
        <div class="modal-top">
            <span class="title">Detalhes do usuário</span>
            <f-icon class="xIcon" @click="byeModal()" icon="fa-solid fa-xmark fa-2xl" />
        </div>
        <div class="user-data">
            <ul>
                <div class="userItem">
                    <span>Nome Completo</span>
                    <li>{{User.fullname}}</li>
                </div>
                 <div class="userItem">
                    <span>CPF</span>
                    <li>{{User.cpf | VMask(cpfMask)}}</li>
                 </div>
                <div class="userItem">
                    <span>Nascimento</span>
                    <li>{{User.birthDate}}</li>
                </div>
            </ul>
            <ul>
                <div class="userItem">
                    <span>Telefone</span>
                    <li>{{User.phone | VMask(phoneMask)}}</li>
                </div>
                <div class="userItem">
                    <span>Contato</span>
                    <li v-show="User.checkZap">Whatsapp</li>
                    <li v-show="User.checkSMS">Email e SMS</li>
                </div>
                <span>Email</span>
                <li>{{User.email}}</li>

            </ul>
        </div>        
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            cpfMask:"###.###.###-##",
            phoneMask:"+55(##)#####-####",
            get:false
            

        }
    },
    props:{
        User:{
            type:Object,
        }
    },

    methods: {
        byeModal(){
            this.$emit("byeModal")
        },

    },
}
</script>

<style scoped>
    .all{
        display:flex;
        justify-content: center;
    }
    .modal-shadow{
        width: 100%;
        height: 43.35vw;
        background-color: rgba(0, 0, 0, 0.527);
        position: absolute;
        z-index: 1;

    }

    .modal-content{
        border-radius: 0.5vw;
        width: 30vw;
        height: 21.5vw;
        top: 4vw;
        background-color: rgb(255, 255, 255);
        position: absolute;
        align-content: center;
        z-index: 5;

    }  
    
    .modal-top{
        width: 100%;
        height: 3.3vw;
        font-weight: 700;
        display: flex;
        justify-content: flex-end;
        padding: 1.5vw 1.5vw 0 0;
    }

    .title{
        margin-right:33%;
    }

    .xIcon{
        width: 1vw;
        height: 1vw;
    }

    .xIcon:hover{
        color:rgb(255, 0, 76);
        border-radius:2vw;
        background-color: rgb(219, 213, 213);
        transform: translateZ(10px) scale(1.5);
    }

    .user-data{
        width: 88%;
        height: 15vw;
        border:solid 2px gray;
        border-style: dashed ;
        margin-left: 2.0vw;
        padding: 2.5vw;
        display:flex;
        justify-content: space-between;
    }

    .userItem{
        margin-bottom: 2vw;
    }

    li{
        list-style: none;
    }

    span{
        font-weight: 700;
    }
    

</style>