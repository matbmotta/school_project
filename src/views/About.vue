<template>
  <div>
    <Nav></Nav>
    <titulo texto="Aluno" />
    <Professor />
  </div>
</template>

<script>
import Professor from "../components/Professor/Professor";
import Nav from "../components/_nav/Nav";
import titulo from "../components/_share/titulo";

export default {
  components: {
    Professor,
    Nav,
    titulo,
  },
};
</script>

<style lang="scss" scoped>
</style>