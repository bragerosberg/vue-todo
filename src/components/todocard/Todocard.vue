<template>
  <div v-bind:class="[task.completed ? 'completed' : 'pending', taskCard]">
    <section v-if="!task.completed" v-on:click="toggleComplete">
      <p>{{ task.title }}</p>
    </section>

    <section v-if="task.completed" v-on:click="toggleComplete">
      <p>{{ task.title }}</p>
      <button @click="$emit('deletetask', task.id)">X</button>
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
.completed {
  background-color: red;
  color: white;
  text-decoration: line-through;
}
.pending {
  background-color: greenyellow;
  color: black;
}
</style>