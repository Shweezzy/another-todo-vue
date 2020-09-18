<template>
  <div>
    <p>number of tasks: {{todos.length}}</p>
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