<script>
import TimesApi from "@/api/times.js";
const timesApi = new TimesApi();
export default {
  data() {
    return {
      time: {},
      times: [],
    };
  },
  async created() {
    this.times = await timesApi.buscarTodosOsTimes();
  },
  methods: {
    async salvar() {
      if (this.time.id){
        await timesApi.atualizarTime(this.time);
      } else {
        await timesApi.adicionarTime(this.time);
      }
      this.times = await timesApi.buscarTodosOsTimes();
      this.time = {};
    },
    async excluir(time) {
      await timesApi.excluirTime(time.id);
      this.times = await timesApi.buscarTodosOsTimes();
    },
    editar(time) {
      Object.assign(this.time, time);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de times</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="time.nome" @keyup.enter="salvar" />
      <button @click="salvar">Adicionar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="time in times" :key="time.id">
            <td>{{ time.id }}</td>
            <td>{{ time.nome }}</td>
            <td>
              <button @click="editar(time)">Editar</button>
              <button @click="excluir(time)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style>
.title {
  text-align: center;
  margin: 2rem 0;
}

.form_input {
  display: flex;
  justify-content: center;
  margin: 2rem 0;
}

.form_input input {
  width: 50%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 10px;
}

.form_input button {
  padding: 0.5rem;
  width: 15%;
  border: 1px solid rgb(195, 81, 206);
  border-radius: 10px;
  background-color: rgb(144, 101, 148);
  color: aliceblue;
  font-weight: bold;
  margin-left: 1%;
}

.list_times {
  display: flex;
  justify-content: center;
}

table {
  width: 50%;
  border-collapse: collapse;
  margin: 0 auto;
  border: 1px solid black;
  font-size: 1.1rem;
  text-align: center;
}

table thead {
  background-color: rgb(103, 159, 207);
  color: white;
}

table tbody tr:nth-child(odd) {
  background-color: rgb(151, 189, 223);
  color: white;
}
</style>
