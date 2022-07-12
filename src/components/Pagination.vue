<template>
    <div>
        <div class="card text-center m-3">



            <div id="usuarios">
                <div>
                    <p id="UserCpf" v-for="item in pageOfItems" v-mask="'###.###.###-##'" :key="item.id">{{ item.cpf | VMask(mask)
 }} <br></p>
                </div>
                <div id="nome">
                    <br>
                    <br>
                    <p id="UserName" v-for="item in pageOfItems"  :key="item.id">{{ item.fullname }} <br>  <i class="fa fa-eye" id="icon" aria-hidden="true"></i> </p>
                </div>
            </div>
                 
            <br>
            <br>
            <hr>
            <br>
        </div>
        <div class="card-footer pb-0 pt-3">
            <jw-pagination :disableDefaultStyles="true" :labels="customLabels" :items="users"
                @changePage="onChangePage"></jw-pagination>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
// an example array of items to be paged
const customLabels = {
    first: '<<',
    last: '>>',
    previous: '<',
    next: '>'
};
export default {
    data() {
        return {
            users: [{}],
            pageOfItems: [],
            customLabels,
            mask: "###.###.###.-##"
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
        }
    }
};
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