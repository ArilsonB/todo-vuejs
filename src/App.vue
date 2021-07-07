<template>
  <div>
    <Header />
    <TodoList />
    <Footer />
  </div>
</template>

<script>

import '@/styles/global.css';

import Header from './components/Header';
import TodoList from './components/TodoList';
import Footer from './components/Footer';

export default {
  name: 'App',
  components: {
    Header,
    TodoList,
    Footer
  }
}
</script>