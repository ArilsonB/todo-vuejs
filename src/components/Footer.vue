<template>
  <footer class="centered">
    <div class="copy">
      <span>&copy; Copyright {{year}} – <a href="https://arilsondev.github.io">Arilson Bolivar</a>. Todos os direitos reservados.</span>
    </div>
  </footer>
</template>

<script>
  export default {
    name: 'Footer',
    data: function(){
      return {
        year: (new Date()).getFullYear(),
      }
    }
  }
</script>

<style scoped>
  footer {
    margin-top: 15px;
    padding-bottom: 20px;
  }
</style>