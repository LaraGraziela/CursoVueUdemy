<template>
  <div class="row">
    <div class="col-sm-12 text-center">
      <h2>Diretivas</h2>
      <!-- V-TEXT CHAMA UMA FUNÇÃO DO JS, MAS PARA MOSTRAR DIRETO É SO USAR: ' TEXTO ' -->
      <p v-text="'V-text: esse é o v-text'"></p>
      <!-- V-HTML É IGUAL O V-TEXT PORÉM POSSO USAR TAGS HTML NELE -->
      <p v-html="'V-html: esse é o <strong>v-html</strong>'"></p>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style></style>
