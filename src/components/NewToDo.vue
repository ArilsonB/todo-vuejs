<template>
  <form
    method="post"
    @submit="addToDo">
    <input
      name="todo"
      v-model="todo"
      placeholder="New To-do" />
    <button type="submit"><i class="fas fa-plus-circle"></i></button>
  </form>
</template>

<script>
  export default {
    name: 'NewToDo',
    data() {
      return {
        todo: '',
      }
    },
    methods: {
      addToDo: function (e){
        e.preventDefault();

        if(this.todo.trim() === ''){
          return;
        }

        const meses = ["Janeiro", "Fevereiro", "Março", "Abril", "Maio", "Junho", "Julho","Agosto","Setembro","Outubro","Novembro","Dezembro"];

        let date = new Date();

        let dataFormatada = (date.getDate() + " de " + meses[date.getMonth()] + " de " + date.getFullYear() + " às " + date.getHours() + ":" + date.getMinutes());

        // 21 de Janeiro de 2021 às 21:22

        this.$emit('add-todo', {
          todo: this.todo,
          time: dataFormatada
        });

        this.todo = '';
      }
    }
  }
</script>

<style scoped>
  form {
    position: relative;
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  input {
    font-size: 25px;
    width: 100%;
    padding: 20px 60px 20px 30px;
    border-radius: 20px;
  }

  button {
    position: absolute;
    right: 0px;
    background: transparent;
    cursor: pointer;
    height: 100%;
    width: 61px;
  }

  button > i {
    font-size: 40px;
    color: #ddd;
    transition: .2s opacity;
  }

  button:hover > i {
    opacity: 0.7;
  }
</style>