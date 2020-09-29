<template>
  <div id="app">
    <article class="app__header">
      <form class="todo__form" @submit="appendTask">
        <input class="todo__form--input" placeholder="Please write your task here" type="text" v-model="title" name="title">
        <button class="todo__form--button" type="submit">Add Todo</button>
      </form>
      <aside class="todolist__buttons"> 
        <button class="todolist__button" @click="deleteAllTasks">Clear List</button>
        <button class="todolist__button" @click="deleteAllComplete">Clear complete</button>
      </aside>
    </article>
    <Todolist v-bind:tasks="tasks" v-on:deletetask="deleteTask"/>
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
* {
  font-family: 'Arial', sans-serif;
  list-style-type: none;
}

button:hover {
  cursor: pointer;
}

.app__header {
  display: flex;
  justify-content: center;
}

.todo__form--input,
.todo__form--button {
  padding: 1em;
  width: 70%;
}

.todo__form--button {
  background: linear-gradient(to left, #11998e, #38ef7d);
  color: white;
}

.todolist__buttons {
  display: flex;
  justify-content: center;
}

.todolist__button {
  background: linear-gradient(to top, #ff416c, #ff4b2b);
  padding: 1em;
  color: white;
}

</style>
