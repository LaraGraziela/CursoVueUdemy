<template>
  <div id="all">
    <h3>Adicionar tarefas</h3>
    <div class="row container-fluid">
      <div class="col-sm-4"></div>
      <div class="col-sm-4">
        <input
          type="text"
          class="form-control"
          v-model="inputTask"
          placeholder="Digite uma tarefa"
          @keydown.enter="addTask"
        /><br />
        <button class="btn btn-success" @click="addTask">Adicionar</button>
        <br /><br />
        <div class="lista">
          <tbody>
            <h4>Tarefas:</h4>
            <tr v-for="task in tasks" :key="task" style="list-style: none;">
              <td class="text-left">{{ task.id }} - {{ task.name }}</td>

              <td class="col-sm-1">
                <button class="btn btn-danger" @click="removeTask(task.id)">
                  x
                </button>
                <hr />
              </td>
            </tr>
          </tbody>
        </div>
      </div>
      <div class="col-sm-4"></div>
    </div>
  </div>

  <!-- CRIANDO UM INPUT CHECKBOX E DEPOIS FAZENDO ELE APARECER EM FORMATO DE LISTA DE ACORDO COM O CLIQUE DO USUÁRIO -->
  <div class="row checkbox">
    <div class="col-sm-6">
      <h3>Checkbox</h3>
      <h5>Selecione os itens que você tem em casa:</h5>

      <!-- CRIANDO A OPÇÃO DE ADICIONAR UM NOVO CHECKBOX -->
      <span>
        <input type="text" v-model="moveisN" @keydown.enter="addMovel" />
        <button class="btn btn-success" @click="addMovel">Adicionar</button>
      </span>
      <br /><br />

      <span>
        <input
          v-model="moveis"
          type="checkbox"
          value="Geladeira"
        />Geladeira</span
      ><br />
      <span
        ><input
          v-model="moveis"
          type="checkbox"
          value="Televisão"
        />Televisão</span
      ><br />
      <span><input v-model="moveis" type="checkbox" value="Fogão" />Fogão</span
      ><br />
      <span
        ><input
          v-model="moveis"
          type="checkbox"
          value="Micro-ondas"
        />Micro-ondas</span
      ><br />
      <span
        ><input
          v-model="moveis"
          type="checkbox"
          value="Cafeteira"
        />Cafeteira</span
      ><br />

      <!-- MOSTRANDO O CHECKBOX DO QUE FOI DIGITADO -->
      <div v-for="novoMovel in moveisLista" :key="novoMovel">
        <input
          v-model="moveis"
          type="checkbox"
          :value="novoMovel"
          :name="novoMovel"
          :id="novoMovel"
        />{{ novoMovel }}
      </div>

      <br />
    </div>

    <div class="col-sm-6">
      <h5>Itens selecionados:</h5>
      <ul>
        <li v-for="movel in moveis" :key="movel">{{ movel }}</li>
      </ul>
    </div>
    <br /><br /><br /><br /><br /><br />
  </div>
</template>

<script>
export default {
  data: () => ({
    tasks: [
      { id: 1, name: "Estudar" },
      { id: 2, name: "Trabalhar" },
      { id: 3, name: "Cuidar da Tula" },
    ],
    inputTask: "",
    moveis: [],
    moveisN: "",
    moveisLista: [],
  }),
  methods: {
    addTask() {
      if (this.inputTask.trim() != "") {
        this.tasks.push({ name: this.inputTask, id: this.tasks.length + 1 });
        this.inputTask = "";
      }
    },
    removeTask(id) {
      for (var i = this.tasks.length; i--; ) {
        if (this.tasks[i].id === id) {
          this.tasks.splice(i, 1);
        }
      }
    },
    //FUNÇÃO QUE COLOCA O MÓVEL DIGITADO NA LISTA APÓS CLICAR NO CHECKBOX
    addMovel() {
      this.moveisLista.push(this.moveisN);
      console.log(this.moveisLista);
    },
  },
};
</script>

<style scoped>
#all {
  text-align: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  padding-bottom: 50px;
}
.lista {
  padding: 20px;
  box-shadow: 1px 1px 10px 1px rgb(168, 168, 168);
  border-radius: 5px;
}
.checkbox {
  padding: 20px;
  box-shadow: 1px 1px 10px 1px rgb(202, 202, 202);
  margin: 20px;
  border-radius: 5px;
}
</style>
