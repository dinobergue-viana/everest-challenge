<template>
<div>
  <div class="content">

  
  <UserCad v-show="swich==false"/>
  <Pagination @SendUser="createModal" v-show="swich==true"/>
  
  </div>
  <UserModal @byeModal="closeModal" :User="userData" v-show="showModal"/>
</div>

</template>

<script>

import Pagination from "@/components/List/Pagination.vue"
import UserCad from "@/components/List/UserCad.vue"
import UserModal from "@/components/UserModal.vue"
  export default {
    
    name: "app",
    components:{
      Pagination,
      UserCad,
      UserModal
    },
    
    methods: {
      createModal(userInfo){
        this.userData = userInfo
        this.showModal = true
      },

      closeModal(){
        this.showModal = false
      }

    },
    data() {
      return {        
        swich:true,
        showModal:false,
        userData:{},
      }
    },

    
  }

</script>

<style scoped>

  *{
    font-size: min(1vw);
  }


.content{
    padding-left: 2em;
    margin-left: 27%;
    width: 45.2vw;
    align-content: center;

  }

.ListSwich{
    margin-bottom: 1vw
  }



</style>