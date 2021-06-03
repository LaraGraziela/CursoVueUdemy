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
              <td>{{ task.id }} - {{ task.name }}</td>

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
</style>
