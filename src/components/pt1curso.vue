<template>
  <div class="div1 container-fluid">
    <br> <br>
    <h1>{{ titulo }}</h1> <!-- COM O V-ONCE O TITULO NAO É ALTERADO -->
    <!--<p>{{saudacao()}}</p>-->

    <input type="text" @input="trocaTexto" /><br><br>
    <!-- ^^ NÃO FUNCIONA POR CAUSA DO V-ONCE -->
    
    <a :href="link">Google</a>

    <br><br><br>
  </div>
</template>

<script>
export default {
  data: () => ({
    titulo: "Isso é Vue!",
    link: 'http://google.com.br',
    
  }),

  methods: {
    trocaTexto(titulo) {
      this.titulo = titulo.target.value;
    },
    //^^ NÃO FUNCIONA POR CAUSA DO V-ONCE 

    /*saudacao () {
      this.titulo = 'Bom dia!'
      return this.titulo
    }*/
  },
};
</script>

<style scoped>

.div1{
  align-items: center;
  text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  box-shadow: 1px 1px 5px 1px rgb(209, 209, 209);
}
</style>
