<template>
  <br />
  <div id="all" class="container-fluid">
    <h2>Parte 2</h2>
    <div class="caixas"></div>

    <div id="div">
      <div class="demo" :class="estilo1" @click="aplicarc1 = !aplicarc1"></div>
      <div class="demo" :class="estilo2" @click="aplicarc2 = !aplicarc2"></div>
      <div class="demo" :class="estilo3" @click="aplicarc3 = !aplicarc3"></div>
    </div>
    <br /><br />
    <hr />

    <div class="demo2" :style="cores"></div>
    <p>Digite uma cor em inglês e um número:</p>
    <input type="text" v-model="cor"/><br>
    <input type="text" v-model="largura">
  </div>  
</template>

<script>
export default {
  data: () => ({
    aplicarc1: false,
    aplicarc2: false,
    aplicarc3: false,

    cor: '',
    largura: 100
  }),

  computed: {
    estilo1() {
      return {
        c1: this.aplicarc1,
      };
    },
    estilo2() {
      return {
        c2: this.aplicarc2,
      };
    },
    estilo3() {
      return {
        c3: this.aplicarc3,
      };
    },

    cores() {
        return {
            backgroundColor: this.cor,
            width: this.largura + 'px'
        }
    }
  },
};
</script>

<style scoped>
#all{
  align-items: center;
  text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
.demo {
  width: 100px;
  height: 100px;
  background-color: rgb(206, 206, 206);
  
}

.demo2{
  width: 100px;
  height: 100px;
  background-color: rgb(206, 206, 206);
 
  
}


#div {
  display: flex;
  justify-content: space-around;
}

.c1 {
  background-color: coral;
}
.c2 {
  background-color: darkgreen;
}
.c3 {
  background-color: deeppink;
}
</style>

