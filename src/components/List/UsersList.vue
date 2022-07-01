<template>
  <div class="swich">
    <span @click="changeCad" :class="cad">CADASTRO</span>
    <span @click="changeList" :class="list" >LISTAGEM</span>

  </div>
</template>

<script>
export default {  
    data() {
        return {
            cad:'off',
            list:'on',
            default: true
        }
    },  
    methods: {
        changeCad(){
            this.cad = 'on'
            this.list = 'off'
            this.default = false
            this.$emit("changeCad",this.default)
        },

        changeList(){
            this.cad = 'off'
            this.list = 'on'
            this.default = true
            this.$emit("changeList",this.default)
        }

    },

}
</script>

<style  scoped>

    .swich{
        display:flex;
        justify-content: space-around;
        width: 22vw;
        height: 1vw;
        margin-top: 10vw;
        margin-left: 10.5vw;
    }

    span{
        width: 22vw;
        height: 1vw;
        text-align: center;

    }

    .off{
        color: rgb(65, 64, 64);
        border-bottom: solid 1px rgb(223, 219, 219);
        font-weight: 70;
    }

    .on{

        font-weight: 700;
        color:black;
        border:solid 1px black;
        border-radius:2vw;
        
        animation-name:turnOn;
        animation-duration: 0.15s;
        animation-fill-mode: forwards;
    }

    @keyframes turnOn{
        from{background-color: white;}
        to{background-color:black; color: white}
    }
    @keyframes  first{
        from{ width: 0px;}
        to{ width: 372px;}
      }




</style>