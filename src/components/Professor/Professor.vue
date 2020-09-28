<template>
  <div>
    <table border="1px">
      <thead>
        <th>Matrícula</th>
        <th>Nome</th>
        <th>Alunos</th>
      </thead>
      <tbody v-if="Professores.length">
        <tr v-for="(professor, index) in Professores" :key="index">
          <td>{{ professor.id }}</td>
          <td>{{ professor.nome }} {{ professor.sobrenome }}</td>
          <td></td>
        </tr>
      </tbody>
      <tfoot v-else>
        Nenhum Aluno Encontrado
      </tfoot>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      Professores: [
        { id: 1, nome: "vinicius" },
        { id: 2, nome: "Matheus" },
        { id: 3, nome: "Lucas" },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
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