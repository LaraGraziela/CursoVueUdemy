<template>
  <div id="all">
      <h2>Instância</h2>

      <h2>{{aula}}</h2>
      <h2>{{modulo}}</h2>

      <button class="btn" @click="alteraA">Alterar Aula</button> |
      <button class="btn" @click="alteraM">Alterar Módulo</button>
      <hr><br>
  </div>
</template>

<script>
export default {
    data: () => ({
        aula: 'Instância Vue',
        modulo: 'Módulo: 5'
    }),

    methods: {
        alteraA() {
         this.aula += ' Vue'
        },

        alteraM() {
            this.modulo +=' JS'
        }
    }

}
</script>

<style scoped>
#all{
    text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
.btn{
    background-color: rgb(51, 201, 108);
    color: white;
}
</style>