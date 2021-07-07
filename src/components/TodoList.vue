<template>
  <main class="container centered">
    <CreateTodo v-on:create-todo="createTodo" />
    <div class="buttons">
      <a 
        href="#"
        v-on:click.prevent="filterTodos('all')">Todos</a>
      <a
        href="#"
        v-on:click.prevent="filterTodos('incomplete')">Incompletos</a>
      <a
       href="#"
       v-on:click.prevent="filterTodos('complete')">Completos</a>
    </div>
    <section class="my_list">
      <div v-if="this.todoList.length === 0" class="empty_msg">
        <i class="fas fa-robot"></i>
        <p>Houston, we have a problem!</p>
        <p>We don't have anything to do today, start creating a new To Do.</p>
      </div>
      <div class="todo_item" v-for="(item, index) in filteredTodos" :key="index">
        <time>
          <i class="far fa-clock"></i>
          <span>Created at {{item.time}}</span>
        </time>
        <a href="#" class="complete" v-on:click.prevent="completeTodo(item)">
          <i class="fas fa-check"></i>
          <span>Completar</span>
        </a>
        <a href="#" class="delete" v-on:click.prevent="deteteTodo(index)">
          <i class="fas fa-times"></i>
          <span>Apagar</span>
        </a>
        <p>{{item.todo}}</p>
      </div>
    </section>
  </main>
</template>

<script>
  import CreateTodo from './CreateTodo';

  export default {
    name: 'TodoList',
    components: {
      CreateTodo
    },
    data: () => {
      return {
        visibility: 'all',
        filters: {
          all: function(todos) {
            return todos;
          },
          complete: function(todos) {
            return todos.filter(function(todo) {
              return todo.completed;
            });
          },
          incomplete: function(todos) {
            return todos.filter(function(todo) {
              return !todo.completed;
            });
          }
        },
        todoList: (JSON.parse(localStorage.getItem('todo-list')) || []),
      }
    },
    methods: {
      createTodo: function(todo){
        this.todoList.push(todo)
      },
      deteteTodo: function(index){
        this.todoList.splice(index, 1);
      },
      completeTodo: function(todo){
        todo.completed = !todo.completed;
      },
      filterTodos: function(filter){
        this.visibility = filter;
      }
    },
    computed: {
      filteredTodos: function () {
        return this.filters[this.visibility](this.todoList);
      }
    },
    watch: {
      todoList: function(todo){
        localStorage.setItem('todo-list', JSON.stringify(todo));
      }
    }
  }
</script>

<style scoped>
 .container {
    display: flex;
    flex-direction: column;
    z-index: 100;
    margin-top: -350px;
  }

  .buttons {
    display: flex;
    flex-direction: row;
    margin: 15px 0;
  }

  .buttons > a {
    background-color: #fff;
    border-radius: 20px;
    padding: 10px 20px;
    margin-right: 15px;
    font-weight: bold;
    color: #555;
  }
  
  .my_list {
    display: flex;
    flex-direction: column;
    margin-top: 5px;
    background: #fff;
    border-radius: 20px;
    min-height: 200px;
    padding: 20px;
    box-shadow: 5px 5px 25px rgba(25,25,25,.2);
  }

  .empty_msg {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: 18px;
  }
  .empty_msg > i {
    font-size: 60px;
    color: #aaa;
    margin-bottom: 10px;
  }

  .todo_item {
    position: relative;
    display: flex;
    flex-direction: column;
    padding: 15px 10px;
    border-bottom: 1px solid #eee;
    margin-bottom: 25px;
    border-radius: 10px;
  }
  .todo_item:hover {
    background: rgba(1223, 231, 253, 0.1);
  }
  .todo_item:last-child {
    border-bottom: 0;
    margin-bottom: 5px;
  }
  .todo_item > time {
    font-size: 12px;
    color: #aaa;
    margin-bottom: 10px;
    font-weight: 100;
  }
  .todo_item > time > i + span {
    margin-left: 5px;
  }
  .todo_item > .delete {
    position: absolute;
    font-size: 12px;
    right: 5px;
    color: red;
    cursor: pointer;
  }
  .todo_item > .delete > i + span {
    margin-left: 5px;
  }
  .todo_item > p {
    display: block;
    word-wrap: break-word;
    word-break: break-all;
    line-height: 1.5;
  }
</style>