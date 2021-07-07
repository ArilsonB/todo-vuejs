<template>
  <div>
    <header>
      <nav class="navbar">
        <div class="nav-container centered">
          <div class="logo-container">
            <a href="#" class="logo" title="Arilson Bolivar: Todo App">
              <h1>VueJS: ToDo</h1>
            </a>
          </div>
        </div>
      </nav>
    </header>
    <div class="header-wave" :style="{ backgroundImage: 'url(' + require('@/assets/wave.svg') + ')' }" />
  </div>
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
    height: 120px;
    background: #e63946;
  }
  .navbar {
    display: flex;
    align-items: center;
    width: 100%;
    height: 60px;
  }
  .nav-container {
    background: transparent
  }
  .logo {
    color: #fff;
  }
  .logo > h1 {
    font-weight: 900;
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