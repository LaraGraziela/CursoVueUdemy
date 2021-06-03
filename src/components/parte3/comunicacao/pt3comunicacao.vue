<template>
  <div class="container text-center">
    <h2>Usuário</h2>
    <p>Componente!</p>
    <hr />
    <p>
      Nome: <strong>{{ nome }} </strong>
    </p>
    <p>
      Idade: <strong>{{ idade }}</strong>
    </p>

    <button class="btn btn-light" @click="alteraNome">Alterar Nome</button>

    <div class="componentes">
      <Apppt3usuarioInfo :nome="nome" />
      <Apppt3usuarioEditar />
    </div>
  </div>
  <br /><br />
</template>

<script>
import Apppt3usuarioInfo from "./pt3usuarioInfo";
import Apppt3usuarioEditar from "./pt3usuarioEditar";
export default {
  components: {
    Apppt3usuarioInfo,
    Apppt3usuarioEditar,
  },

  data: () => ({
    nome: "Pedro",
    idade: 21,
  }),

  methods: {
    alteraNome() {
      if (this.nome == "Ana") {
        this.nome = "Pedro";
      } else {
        this.nome = "Ana";
      }
    },
  },
};
</script>

<style scoped>
.container {
  background-color: brown;
  color: white;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 0px 10px 15px 0px rgb(148, 148, 148);
}

.container hr {
  margin: 20px 10px;
}

.componentes {
  display: flex;
}

.componentes > * {
  margin: 10px;
}
</style>
