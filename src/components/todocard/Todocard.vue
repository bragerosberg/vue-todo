<template>
  <div v-bind:class="[todo.completed ? 'completed' : 'pending', taskCard]">
    <section v-if="!todo.completed" v-on:click="toggleComplete">
      <p>{{ todo.title }}</p>
    </section>

    <section v-if="todo.completed" v-on:click="toggleComplete">
      <p>{{ todo.title }}</p>
      <button @click="$emit('deletetask', todo.id)">X</button>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Todocard',
  props: [
    "todo"
  ], methods: {
    toggleComplete() { this.todo.completed = !this.todo.completed}
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