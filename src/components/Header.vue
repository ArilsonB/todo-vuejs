<template>
  <header>
    <nav class="navbar">
      <div class="nav-container">
        <a href="#" class="logo">
          <h1>ToDo App VueJS</h1>
        </a>
      </div>
    </nav>
  </header>
  <div class="header-wave" :style="{ backgroundImage: 'url(' + require('@/assets/wave.svg') + ')' }" />
</template>

<script>
  export default {
    name: 'Header',
  }
</script>

<style scoped>
  header {
    display: flex;
    flex-direction: column;
    width: 100vw;
    height: 100px;
    background: #e63946;
  }
  .navbar {
    display: flex;
    align-items: center;
    width: 100%;
    height: 60px;
  }

  .logo {
    color: #fff;
  }

  .logo > h1 {
    font-weight: 900;
  }

  .nav-container {
    width: 800px;
    margin: 0 auto;
  }

  .header-container {
    margin: 0 auto;
    width: 800px;
  }

  .header-wave {
    background-repeat: no-repeat;
    background-size: contain;
    position: relative;
    display: block;
    height: 320px;
    z-index: -10;
    margin-top: -1px;
    width: 100%;
    overflow: hidden;
  }

</style>