<template>
  <div>
    <h1>{{nome}}</h1>
    <input type="text" placeholder="Nome do Aluno" v-model="nome">
    
  </div>
</template>

<script>
export default {
  props: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
