<template>
  <div id="home">
    <AddTodo v-on:add-todo="addTodo"/>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <Test testProps="Welcome to My First Vue.js App"/> -->
    <Todolist v-bind:todoitems="todos" v-on:del-todo="delTodo"/>
  </div>
</template>

<script>
import AddTodo from '../components/AddTodo.vue';
import Todolist from '../components/Todolist.vue';
import axios from 'axios'; 

export default {
  name: 'Home',
  components: {
    AddTodo,
    Todolist
  },
  methods: {
    delTodo(id) {
      console.log(id);
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todos = this.todos.filter(todo => todo.id != id))
      .catch(e => onsole.log(e));

    },
    addTodo(newTodoItem) {
      const { title, completed } = newTodoItem;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title : title,
        completed : completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(e => onsole.log(e));

      //this.todos = [...this.todos, newTodoItem];
    }
  },
  data() {
    return {
      todos: []
    }
  },
  created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(e => onsole.log(e));
  }
}
</script>

<style>
#home {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
}
</style>
