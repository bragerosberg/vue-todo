<template>
  <div>
    <article>
      <form @submit="appendTask">
        <input type="text" v-model="title" name="title">
        <button type="submit">Add Todo</button>
      </form>
    </article>

    <section>
      <h2>Todo</h2>
      <ul>
        <li v-bind:key="todo.id" v-for="todo in todos">
          <Todocard v-bind:todo="todo" v-on:deletetask="$emit('deletetask', todo.id)"/>
        </li>
      </ul>
      <button @click="$emit('cleartasks')">Clear List</button>
      <button @click="$emit('clearcomplete')">Clear complete</button>
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
      const newTask = {
        id: uuid(),
        title: this.title,
        completed: false
      }
      this.$emit('add-todo', newTask);
      this.clearInputField();
    },
  }
}

</script>
<style scoped>
</style>