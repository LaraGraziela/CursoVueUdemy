<template>
  <div id="all">
    <h2>Condicionais</h2>
    <h3>Login</h3>

    <template v-if="logado">
      <p v-if="logado">Usuário logado: {{ nome }}</p>
      <p>Perfil: Admin</p>
    </template>

    <p v-else-if="anonimo">Navegando como anônimo.</p>
    <!-- POSSO USAR O V-ELSE TAMBÉM MAS SÓ SE ACIMA TIVER UM V-IF -->
    <p v-if="!logado">Nenhum usuário logado.</p>

    <button class="btn" @click="logado = !logado">{{ logado ? "Sair" : "Entrar" }}</button>

    <input type="checkbox" v-model="anonimo" checked/>
    <hr/>
    
    <!-- V-SHOW: -->
    <footer v-show="logado">Desenvolvido para você!</footer>
    <footer v-show="!logado">Desenvolvido para você, desconhecido!</footer>
    <br><hr>

    <!-- LISTA: -->
    <h3 class="ul">Lista:</h3>
    <p class="ul">Cores:</p>
    <!-- MOSTRAR AS CORES COM O ÍNDICE (PODE COLOCAR NA ORDEM QUE QUISER)-->
    <ul class="ul">
      <li :key="cor" v-for="(cor,i) in cores">{{i + 1}}- {{cor}}</li>
    </ul>

    <button class="ul btn" @click="cores.push('preto')">Adicionar</button>
    <br><hr>

    <p class="ul">Pessoas:</p>
    
    <ul class="ul">
      <li :key="pessoa" v-for="pessoa in pessoas">
        <!-- {{pessoa.nome}} -->

        <!-- MOSTRA TODO O CONTEÚDO DO ARRAY, GERA ECONOMIA DE CÓDIGO -->
        <div :key="valor" v-for="(valor,chave) in pessoa">
          {{chave}}: {{valor}} 
        </div>
      </li>
    </ul>
    <hr>
    
    <!-- MOSTRAR UM ARRAY DE 1 A 10 -->
    <span :key="n" v-for="n in 10">{{n}}</span><br><br><hr><br>

  </div>
</template>

<script>
export default {
  data: () => ({
    nome: "Lara",
    logado: false,
    anonimo: true,

    //LISTA:
    cores: ['vermelho', 'verde', 'amarelo', 'rosa'],
    pessoas: [
      {Nome: 'Lara', Idade: 20, Peso: 70},
      {Nome: 'Natan', Idade: 28, Peso: 80} 
    ]
  }),

  
};
</script>

<style scoped>
  .ul{
    /* TIRAR AS BOLINHAS QUE VEM NA LISTA*/
    list-style: none;
    text-align: center;
  
  }

  #all{
  text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  }
  .btn{
    background-color: rgb(51, 201, 108);
    color: white;
    
}
</style>