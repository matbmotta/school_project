<template>
  <div>
    <Nav></Nav>
    <titulo texto="Aluno" />
    <input
      type="text"
      placeholder="Nome do Aluno"
      v-model="nome"
      v-on:keyup.enter="addAluno()"
    />

    <table border="1px">
      <thead>
        <th>Matrícula</th>
        <th>Nome</th>
        <th>Opções</th>
      </thead>
      <tbody v-if="alunos.length">
        <tr v-for="(aluno, index) in alunos" :key="index">
          <td>{{ aluno.id }}</td>
          <td>{{ aluno.nome }} {{ aluno.sobrenome }}</td>
          <td>
            <button class="btn" @click="remove(aluno)">Remover</button>
          </td>
        </tr>
      </tbody>
      <tfoot v-else>
        Nenhum Aluno Encontrado
      </tfoot>
    </table>
  </div>
</template>


<script>
import titulo from "../components/_share/titulo";
import Nav from "../components/_nav/Nav";

export default {
  components: {
    titulo,
    Nav,
  },
  data() {
    return {
      titulo: "Aluno",
      nome: "",
      alunos: [],
    };
  },
  created() {
    this.$http
      .get("http://localhost:3000/alunos")
      .then((res) => res.json())
      .then((alunos) => (this.alunos = alunos));
  },
  methods: {
    addAluno() {
      let _aluno = {
        nome: this.nome,
        sobrenome: "",
      };

      this.$http
        .post("http://localhost:3000/alunos", _aluno)
        .then((res) => res.json());
      // .then((alunoRetornado) => {
      //   this.alunos.push(aluno);
      //   this.nome = "";

      this.alunos.push(_aluno);
      this.nome = "";
    },
    remove(aluno) {
      this.$http.delete(`http://localhost:3000/alunos/${aluno.id}`).then(() => {
        let indice = this.alunos.indexOf(aluno);
        this.alunos.splice(indice, 1);
      });
    },
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");

.btn {
  background-color: #fa4430;
  padding: 10px 20px;
  cursor: pointer;
  border: 2px solid black;
  color: white;
  font-weight: bold;
  border-radius: 5px;
}

.btn:hover {
  text-shadow: 1px 1px 1px black;
}

body {
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}
body,
html {
  margin: 0;
  height: 100%;
}

table {
  margin: 0px;
  padding: 0px;
  list-style-type: none;
  width: 100%;
}
table tr td {
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  margin-bottom: 2px;
  color: #3e5252;
}
table thead th {
  background-color: rgb(184, 208, 216) !important;
  font-size: 1.2em;
  padding: 10px 0px;
  text-align: center !important;
}
.colPequeno {
  width: 5%;
}
</style>
