<template>
  <div v-bind:class="[task.completed ? 'completed' : 'pending', taskCard]">
    <section v-if="!task.completed" v-on:click="toggleComplete">
      <p>{{ task.title }}</p>
    </section>

    <section class="completed__wrapper" v-if="task.completed" v-on:click="toggleComplete">
      <button class="btn" @click="$emit('deletetask', task.id)">X</button>
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

.btn {
  float: right;
}

.pending {
  background-color: gainsboro;
  color: black;
}
</style>