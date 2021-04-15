<template>
    <div id="all" class="container-fluid">
        <br>
        <hr>
        <h2>Desafios 4</h2>

        <div id="desafio3"></div>
        <p>Clique para ativar:</p>
        <button class="btn" @click="efeito">Efeito</button>
        <div id="efeito" :class="classe1"></div><br><br>

        <p>Digite "quadrado" e "perigo":</p>  
        <input type="text" v-model="classe3">  
        <div :class="classe3"></div><br><br><hr>
    </div>

</template>

<script>
export default {
    data: () => ({
        classe1: 'destaque',
        perigo: true,
        classe3: '',
        
    }),
    
    methods: {
        efeito() {
            setInterval(() => {
                this.classe1 = this.classe1  == 'destaque'
                ? 'encolher' : 'destaque'
            }, 1000)
        },

    }

}
</script>

<style scoped>
#all{
  text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
#efeito {
    width: 100px;
    height: 100px;
    border: 1px solid black;
     
}
.destaque{
    background-color: blue;
    width: 200px !important;
}
.encolher {
    background-color:  rgb(255, 251, 0);
    width: 50px !important;
}
.perigo{
    background-color: red;
}
.quadrado{
    width: 100px;
    height: 100px;
}
.btn{
    background-color: rgb(51, 201, 108);
    color: white;
}



</style>