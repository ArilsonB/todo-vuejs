<template>
  <footer class="container">
    <span>&copy; Copyright {{year}} by Arilson Bolivar. Todos os direitos reservados.</span>
  </footer>
</template>

<script>
  export default {
    name: 'Footer',
    data: () => {
      return {
        year: (new Date()).getFullYear()
      }
    },
  }
</script>

<style scoped>
  .container {
    padding-bottom: 10px;
    margin-top: 15px;
    font-size: 15px;
  }
</style>