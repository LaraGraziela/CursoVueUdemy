<template>
  <div class="componente">
    <h2>Informações de Usuário</h2>
    <p>Vários detalhes...</p>

    <p>Nome do usuário: <strong>{{nome}}</strong></p>
    
    
  </div>
</template>

<script>
export default {
  props: {
    nome: {
      type: String,
      
    },
    
  },
}
</script>

<style scoped>
.componente {
  flex: 1;
  background-color: darkorange;
  color: white;
  padding: 10px;
  border-radius: 5px;
}

</style>