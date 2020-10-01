<template>
  <div>Number of tasks:{{todos.length}}</div>
</template>

<script>
export default {
  props: {
    todos: {
      type: [Array],
      required: true,
    },
  },
};
</script>

<style>
</style>