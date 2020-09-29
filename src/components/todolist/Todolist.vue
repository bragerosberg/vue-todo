<template>
  <div>
    <section>
      <aside class="todolist__buttons"> 
        <button @click="$emit('cleartasks')">Clear List</button>
        <button @click="$emit('clearcomplete')">Clear complete</button>
      </aside>
      <h2>Todo</h2>
      <ul>
        <li v-bind:key="task.id" v-for="task in tasks">
          <Todocard v-bind:task="task" v-on:deletetask="$emit('deletetask', task.id)"/>
        </li>
      </ul>
    </section>

  </div>
</template>
<script>

import Todocard from '../todocard/Todocard';

export default {
  name: 'todolist',
  data() {
    return{
      title: ''
    }
  },
  components: {
    Todocard
  },
  props: [
    "tasks"
  ]
}

</script>
<style scoped>

.todolist__buttons {
  margin-top: 1em;
  display: flex;
  justify-content: center;
}
</style>