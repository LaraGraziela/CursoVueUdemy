<template>
  <h1>Componente filho</h1>

  <div>
      <h2>{{titulo}}</h2>
      <componenteFilho :dados="mensagem" :dados3="objMensagem"> </componenteFilho>
  </div>
  
  <div class="bg-cinza">
      <h3>{{mensagem}}</h3>
      <p>{{dados}}</p>
      <hr>
      <p>{{dados2}}</p>
      <hr>
      <p>{{dados3.name}} {{dados3.from</p>
  </div>
</template>

<script>
export default { 
    props: {
        dados: {
            type: String,
            required: true,
            default: 'Não há mensagem.'
        },
        dados2: {
            type: String,
            required: true,
            default: 'Sou o valor default da prop'
        },
        dados3: {
            type: Object,
            required: true,
            default: {name: 'Sou o default'},
            
        }
    },

    data: () => ({
        mensagem: 'Sou o componente filho',
        titulo: 'Passando Props',
    })

}
</script>

<style>

</style>