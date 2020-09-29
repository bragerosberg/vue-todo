<template>
  <div v-bind:class="[task.completed ? 'completed' : 'pending', taskCard]">
    <section class="task" v-if="!task.completed" v-on:click="toggleComplete">
      <p>{{ task.title }}</p>
    </section>

    <section class="task" v-if="task.completed" v-on:click="toggleComplete">
      <button class="task__delete" @click="$emit('deletetask', task.id)">X</button>
      <p>{{ task.title }}</p>
    </section>
  </div>
</template>

<script>
export default {
  name: 'todocard',
  props: [
    "task"
  ], methods: {
    toggleComplete() { this.task.completed = !this.task.completed}
  }
}
</script>

<style scoped>
.pending,
.completed {
  border: 1px solid black;
  margin-bottom: 1em;
}

.completed {
  background-color: darkgray;
  color: white;
}

.task__delete {
  float: right;
}

.task p{
  margin: 0;
  padding: 1em;
}

.pending {
  background-color: gainsboro;
  color: black;
}
</style>