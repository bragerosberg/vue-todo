<template>
  <div id="app">
    <article>
      <form class="todo__form" @submit="appendTask">
        <input class="todo__form--input" placeholder="Please write your task here" type="text" v-model="title" name="title">
        <button class="todo__form--button" type="submit">Add Todo</button>
      </form>
    </article>
    <Todolist v-bind:tasks="tasks" v-on:clearcomplete="deleteAllComplete" v-on:cleartasks="deleteAllTasks" v-on:deletetask="deleteTask"/>
  </div>
</template>

<script>
import { uuid } from 'uuidv4';
import Todolist from './components/todolist/Todolist';
export default {
  name: 'app',
  components: {
    Todolist,
  },
  data() {
    return {
      tasks: [],
      title: '',
    }
  }, methods: {
    addTodo(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
    deleteAllTasks() {
      this.tasks = [];
    },
    deleteAllComplete() {
      this.tasks = this.tasks.filter(task => !task.completed);
    },
    clearInputField() { this.title = '' },
    appendTask(e) {
      e.preventDefault();
      if (this.title !== '') {
        const newTask = {
          id: uuid(),
          title: this.title,
          completed: false
        }
        this.addTodo(newTask);
        this.clearInputField();
      }
    },
  }
}
</script>
<style>
.todo__form {
  text-align: center;
  background-color: azure;
}

.todo__form--input,
.todo__form--button {
  padding: 1em;
}

.todo__form--button {
  background: linear-gradient(to left, #11998e, #38ef7d);
  color: white;
}

</style>
