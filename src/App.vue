<template>
  <div id="app">
    
    <Navbar />
    <UserSwich  @changeCad="change" @changeList="change" />
    <div class="view-container">
      <router-view/>
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue"
import UserSwich from "@/components/List/UserSwich.vue"

export default {
  name: 'App',
  data() {
    return {
      headerTitle: "Usuários"
    }

  },
  components: {
    Navbar,
    UserSwich
  },
  methods: {
    change(value){
      if(value == false){
        this.$router.push("/register")
      }
      else{
        this.$router.push("/")
      }
        
      },
  },
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}

.ListSwich{
    margin:0vw 0vw 1vw 5vw
  }
</style>
