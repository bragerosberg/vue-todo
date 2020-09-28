<template>
  <div>
    <article>
      <form class="todo__form" @submit="appendTask">
        <input class="todo__form--input" placeholder="Please write your task here" type="text" v-model="title" name="title">
        <button class="todo__form--button" type="submit">Add Todo</button>
      </form>
    </article>

    <section>
      <aside class="todolist__buttons"> 
        <button @click="$emit('cleartasks')">Clear List</button>
        <button @click="$emit('clearcomplete')">Clear complete</button>
      </aside>
      <h2>Todo</h2>
      <ul>
        <li v-bind:key="todo.id" v-for="todo in todos">
          <Todocard v-bind:todo="todo" v-on:deletetask="$emit('deletetask', todo.id)"/>
        </li>
      </ul>
    </section>

  </div>
</template>
<script>

import { uuid } from 'uuidv4';
import Todocard from '../todocard/Todocard';

export default {
  name: 'Todos',
  data() {
    return{
      title: ''
    }
  },
  components: {
    Todocard
  },
  props: [
    "todos"
  ], methods: {
    clearInputField() { this.title = '' },
    appendTask(e) {
      e.preventDefault();
      if (this.title !== '') {
        const newTask = {
          id: uuid(),
          title: this.title,
          completed: false
        }
        this.$emit('add-todo', newTask);
        this.clearInputField();
      }
    },
  }
}

</script>
<style scoped>
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

.todolist__buttons {
  margin-top: 1em;
  display: flex;
  justify-content: center;
}
</style>