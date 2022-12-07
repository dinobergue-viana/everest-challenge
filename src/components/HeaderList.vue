<template>
  <header>
    <div class="buttons">
      <router-link to="/register"> <a class="Cadastro">Cadastro</a></router-link>
      <router-link to="/"> <a class="Listagem">Listagem</a></router-link>
    <router-link to="/register">  <button class="btn">Cadastrar Novo Usuario</button></router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style scoped>
.Cadastro {
  color: #000000;
  font-size: 19px;
  margin-left: 43%;
  transition-duration: 0.3s;
  cursor: pointer;
}

.Cadastro:hover {
  color: rgb(140, 130, 130);
}

.Listagem {
  color: rgb(0, 0, 0);
  font-size: 19px;
  margin-left: 5%;
}
.Listagem:hover {
  color: rgb(140, 130, 130);
 }

.buttons {
  margin-top: 7%;
}

.btn {
  border: solid 2px rgb(255, 35, 123);
  background-color: white;
  color: rgb(0, 0, 0);
  padding: 16px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 16px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
  border-radius: 11px;
  margin-left: 60%;
}

.btn:hover {
  background-color: rgb(255, 35, 123);
  color: white;
}
</style>