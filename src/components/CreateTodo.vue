<template>
  <div class="create_todo">
    <form
      method="post"
      @submit="submitTodo">
      <input 
        name="todo"
        type="text"
        placeholder="Create a todo now..."
        v-model="todo" />
      <button type="submit">
        <i class="fas fa-plus-circle"></i>
      </button>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'CreateTodo',
    data: function(){
      return {
        todo: '',
      }
    },
    methods: {
      submitTodo: function(e){
        e.preventDefault();
        if(this.todo.trim() === ""){
          return;
        }

         const meses = ["Janeiro", "Fevereiro", "Março", "Abril", "Maio", "Junho", "Julho","Agosto","Setembro","Outubro","Novembro","Dezembro"];
        let date = new Date();
        let dataFormatada = (date.getDate() + " de " + meses[date.getMonth()] + " de " + date.getFullYear() + " às " + date.getHours() + ":" + (date.getMinutes() < 10 ? '0' + date.getMinutes() : date.getMinutes()));

        this.$emit('create-todo', {
          todo: this.todo,
          time: dataFormatada,
          completed: false
        });

        this.todo = "";
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
    padding: 15px 60px 15px 30px;
    background-color: rgba(255,255,255,0.9);
    border-radius: 20px;
    box-shadow: 0 0 5px rgba(25,25,25,.25);
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
    color: #bbb;
    transition: .2s opacity;
  }
  button:hover > i {
    opacity: 0.7;
  }
</style>