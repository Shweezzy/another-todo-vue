<template>
  <button class="deleteTodo" @click="removeTodo">X</button>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    removeTodo(e) {
      let indexOfArray = e.target.previousSibling.previousSibling.textContent;
      this.todos.splice([indexOfArray - 1], 1);
    },
  },
};
</script>

<style>
</style>