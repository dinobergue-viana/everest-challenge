<template>
    <div id="usuarios">
        <div>
            <p id="UserCpf" v-for="i in users" :key="i.id">{{ i.cpf }} <br></p>
        </div>
        <div id="nome">
            <br>
            <br>
            <br>
            <br>
            <p id="UserName" v-for="i in users" :key="i.id"> <br>{{ i.fullname }} <br></p>
        </div>
    </div>
</template>

<script>

import axios from 'axios'

export default {
    data() {
        return {
            users: [{}]
        }
    },
    created() {
        this.users = axios.get("/api/users/")
            .then((res) => this.users = res.data)
            .then((json) => {
                this.users = json.users

            })
    }
}
</script>

<style scoped>
#usuarios {
    display: inline-flex;
    margin-top: -84px;
    margin-left: 23%;
    justify-content: center;
    align-items: flex-end;
}


#UserCpf {
    margin-left: 17%;
    margin-top: 42%;
}

#UserName {
    margin-left: -216%;
    margin-top: 35%;
    padding-left: 108%;
}

#nome {
    margin-left: 107%;
    margin-top: -7%;
    padding-left: 8%;

}
</style>