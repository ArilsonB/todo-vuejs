<template>
  <main class="container">
    <NewToDo v-on:add-todo="addToDo" />
    <div class="to-dos">
      <div v-if="todos.length == 0" class="empty_msg">
        <i class="fas fa-robot"></i>
        <p>Houston, we have a problem!</p>
        <p>We don`t have anything to do today.</p>
      </div>
      <div class="to-do" v-for="(item,index) in todos" :key="index">
        <time>
          <i class="far fa-clock"></i>
          <span>Created at {{item.time}}</span>
        </time>
        <a href="#" class="delete" v-on:click.prevent="deleteToDo(index)">
          <i class="fas fa-times"></i>
          <span>Apagar</span>
        </a>
        <p>{{item.todo}}</p>
      </div>
    </div>
  </main>
</template>

<script>
  import NewToDo from './NewToDo';

  let savedTodos = localStorage.getItem('todos') ? localStorage.getItem('todos') : [];

  export default {
    name: 'ToDos',
    data: function() {
      return {
        todos: savedTodos
      };
    },
    methods: {
      deleteToDo(index){
        this.todos.splice(index, 1);
        localStorage.setItem('todos', JSON.stringify(this.todos));
      },
      addToDo(todo) {
        this.todos.push(todo);
        localStorage.setItem('todos', JSON.stringify(this.todos));

        console.log(savedTodos);
      }
    },
    /*computed: {
      allTodos(){
        return this.todos.map(todo => ({
          ...todo
        }))
      }
    },*/
    watch: {
      todos(val){
        console.log('val ', val);
      }
    },
    components: {
      NewToDo
    },
  }
</script>

<style scoped>
  .container {
    display: block;
    z-index: 100;
    margin-top: -320px;
  }


  .to-dos {
    display: flex;
    flex-direction: column;
    margin-top: 30px;
    background: #fff;
    border-radius: 20px;
    min-height: 200px;
    padding: 20px;
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

  .to-do {
    position: relative;
    display: flex;
    flex-direction: column;
    padding: 15px 10px;
    border-bottom: 1px solid #eee;
    margin-bottom: 25px;
    border-radius: 10px;
  }

  .to-do:hover {
    background: rgba(1223, 231, 253, 0.1);
  }

  .to-do:last-child {
    border-bottom: 0;
    margin-bottom: 5px;
  }

  .to-do > time {
    font-size: 12px;
    color: #aaa;
    margin-bottom: 10px;
    font-weight: 100;
  }

  .to-do > time > i + span {
    margin-left: 5px;
  }

  .to-do > .delete {
    position: absolute;
    font-size: 12px;
    right: 5px;
    color: red;
    cursor: pointer;
  }

  .to-do > .delete > i + span {
    margin-left: 5px;
  }

  .to-do > p {
    display: block;
    word-wrap: break-word;
    word-break: break-all;
    line-height: 1.5;
  }

  .header-wave {
    position: absolute;
    top: 0px;
    width: 200px;
  }
</style>