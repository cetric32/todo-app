<template>
  <div id="app">
    <Header></Header>
    <AddTodo @add-todo="addTodo"></AddTodo> 
    <Todos 
    :todos='todos'
    @del-todo="deleteTodo"
    ></Todos>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo';
import Todos from './components/Todos';
import Header from './components/layout/Header';

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data(){
    return {
      todos: [
        {
          id:1,
          title:'Todo one',
          completed: false
        },
        {
          id:2,
          title:'Todo two',
          completed: true
        },
        {
          id:3,
          title:'Todo three',
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id );
    },
    addTodo(newTodo){
      this.todos = [...this.todos,newTodo];
    }
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
  #app {  
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
