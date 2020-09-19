<template>
  <div>
    <div v-for="(todo, i) in todos" :key="todo.id">
      <p class="todoP">
        <span class="todoId">{{ i + 1 }}.</span>
        <span class="todoText" :class="{ isComplete: todo.isComplete }">{{
          todo.text
        }}</span>
        <button class="deleteTodo" @click="removeItem(i)">X</button>
        <input v-model="todo.isComplete" type="checkbox" class="modelCheck" />
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
.todoP {
  font-family: "Monotype Corsiva", sans-serif;
}
#todoText {
  font-size: 18px;
  text-transform: capitalize;
  font-family: "Monotype Corsiva", sans-serif;
}
.todoText {
  font-size: 1.5em;
}
.todoId {
  font-size: 1.5em;
}
.deleteTodo {
  height: 20px;
  float: right;
  border-radius: 5px;
  border: 1px solid silver;
}
</style>
