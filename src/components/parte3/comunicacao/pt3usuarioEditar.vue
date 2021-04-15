<template>
  <div class="componente">
    <h2>Alterar os dados de Usuário</h2>
    <p>Edite as informações</p>
    <p>Idade do Usuário: <strong>{{idade}}</strong></p>
    <button class="btn btn-light" @click="alteraIdade">Alterar Idade</button>
  </div>
</template>

<script>
export default {
  props: ['idade'],
  methods: {
    alteraIdade() {
      this.idade = 33
    }
  }

}
</script>

<style scoped>
.componente {
  background-color: darkolivegreen;
  flex: 1;
  padding: 10px;
  border-radius: 5px;
}

</style>