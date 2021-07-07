<template>
  <Header />
  <ToDos />
  <Footer />
</template>

<script>

import './styles/global.css';

import Header from './components/Header.vue';
import ToDos from './components/ToDos.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    ToDos,
    Footer
  }
}
</script>
