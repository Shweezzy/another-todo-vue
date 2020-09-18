<template>
  <div>
    <div v-for="(todo, i) in todos" :key="todo.id">
      <p>
        <span class="todoId">{{ i +1 }}.</span>
        <span class="todoText" :class="{isComplete: todo.isComplete}">{{ todo.text }}</span>
        <input v-model="todo.isComplete" type="checkbox" class="modelCheck" />
        <button class="deleteTodo" @click="removeItem(i)">X</button>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "todoList",
  props: {
    todos: {
      type: [Array],
      required: true,
    },
    removeTodo: {
      type: Function,
    },
  },
  methods: {
    removeItem(index) {
      this.$emit("removeTodo", index);
    },
  },
};
</script>
<style scoped>
</style>
