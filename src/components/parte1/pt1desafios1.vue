<template>
  <div id="all">
    <br />
    <h2>Desafio 1</h2>

    <p>Meu nome é {{ nome }} e eu tenho {{ idade }} anos.</p>

    <p>Minha idade multiplicada por 3 é: {{ idadeV3() }}</p>

    <p>Mostrando um número entre 0 e 1: {{ random() }}</p>

    <p>Imagem:</p>
    <img :src="imagem" alt="" height="100" /><br /><br />

    <p>Input com o meu nome:</p>
    <input type="text" :value="nome" />
  </div>
  <hr />
</template>

<script>
export default {
  data: () => ({
    nome: "Lara",
    idade: 20,
    imagem: "http://files.cod3r.com.br/curso-vue/vue.jpg",
  }),

  methods: {
    idadeV3() {
      return this.idade * 3;
    },
    random() {
      return Math.random();
    },
  },
};
</script>

<style scoped>
#all {
  align-items: center;
  text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
</style>
