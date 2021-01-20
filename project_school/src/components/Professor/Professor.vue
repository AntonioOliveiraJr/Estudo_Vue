<template>
  <div>
    <titulo texto="Professores" />
    <div></div>

    <table>
      <thead>
        <th>Cód.</th>
        <th>Nome</th>
        <th>Alunos</th>
      </thead>
      <tbody v-if="professores.length">
        <tr v-for="(professor, index) in professores" :key="index">
          <td class="colPequeno">{{ professor.id }}</td>
          <router-link v-bind:to="`/alunos/${professor.id}`" tag="td" style="cursor: pointer">
            {{ professor.nome }} {{ professor.sobrenome }}
          </router-link>
          <td class="colPequeno">
            {{ professor.qtdAlunos }}
          </td>
        </tr>
      </tbody>
      <tfoot v-else>
        Nenhum Professor Encontrado
      </tfoot>
    </table>
  </div>
</template>

<script>
import Titulo from "../_share/Titulo.vue";

export default {
  components: {
    Titulo,
  },
  data() {
    return {
      professores: [],
      Alunos: [],
    };
  },
  created() {
    this.$http
      .get("http://localhost:3000/alunos")
      .then((res) => res.json())
      .then((alunos) => {
        this.Alunos = alunos;
        this.carregarProfessores();
      });
  },
  props: {},
  methods: {
    pegarQuantidadeAlunosPorProfessor() {
      this.professores.forEach((professor, index) => {
        professor = {
          id: professor.id,
          nome: professor.nome,
          qtdAlunos: this.Alunos.filter(
            (aluno) => aluno.professor.id == professor.id
          ).length
        };
        this.professores[index] = professor;
      });
    },
    carregarProfessores() {
      this.$http
        .get("http://localhost:3000/professores")
        .then((res) => res.json())
        .then((professor) => {
          this.professores = professor;
          this.pegarQuantidadeAlunosPorProfessor();
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.colPequeno{
  text-align: center;
  width: 15%
}
</style>
