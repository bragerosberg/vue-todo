<template>
  <div>
    <section>
      <ul class="todolist">
        <li v-bind:key="task.id" v-for="task in tasks">
          <Todocard v-bind:task="task" v-on:deletetask="$emit('deletetask', task.id)"/>
        </li>
      </ul>
    </section>
    <section v-if="!tasks.length > 0">
      <p class="information">There are currently no tasks added, add one above to see it here</p>
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
.todolist {
  padding: 0;
}
.information {
  text-align: center;
}

</style>