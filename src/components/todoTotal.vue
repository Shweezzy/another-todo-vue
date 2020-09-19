<template>
  <div>
    <p id="tasksNumber">number of tasks: {{ todos.length }}</p>
  </div>
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
<style scoped>
#tasksNumber {
  display: inline;
}
</style>
