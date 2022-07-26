<template>
    <header>
        <div class="navbar">
            <div class="nav-container">
                <i class="fa fa-arrow-left" id="custom" aria-hidden="true"></i>
                <h3 class="text">Cadastro de Usuario</h3>
            </div>
        </div>
    </header>
</template>
<script>

</script>
<style scoped>
* {
    box-sizing: border-box;
    margin: 0;
    color: white;
}

.text {
    cursor: pointer;
    margin-left: 39vw;
    margin-top: 15px;
}

.logo {
    cursor: pointer;
    margin-right: -5%;
}

.logo:hover {
    -ms-transform: scale(1.1);
    -webkit-transform: scale(1.1);
    transform: scale(1.1);
}

.navbar {
    background-color: #df1160;
    padding-top: 0rem;
    padding-bottom: 0rem;
    width: 100%;
}

.nav-container {
    font-family: 'Source Sans Pro', sans-serif;
    justify-content: center;
    display: inline-flex;
}

#custom {
    font-size: 33px;
    color: azure;
    margin-left: 23px;
    margin-top: 8px;
}
</style>