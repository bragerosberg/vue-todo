<template>
  <div id="app">
    <Todolist v-bind:todos="todos" v-on:clearcomplete="deleteAllComplete" v-on:cleartasks="deleteAllTasks" v-on:deletetask="deleteTask" v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
import Todolist from './components/todolist/Todolist';
export default {
  name: 'app',
  components: {
    Todolist,
  },
  data() {
    return {
      todos: []
    }
  }, methods: {
    addTodo(newTask) {
      this.todos = [...this.todos, newTask];
    },
    deleteTask(id) {
      this.todos = this.todos.filter(task => task.id !== id);
    },
    deleteAllTasks() {
      this.todos = [];
    },
    deleteAllComplete() {
      this.todos = this.todos.filter(task => !task.completed);
    }
  }
}
</script>

<style>
</style>
