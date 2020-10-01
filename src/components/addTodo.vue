<template>
  <div>
    <input
      @keyup.enter="addItem()"
      class="inputText"
      type="text"
      v-model="todoModel"
      placeholder="type todo..."
    />
    <button @click="addTodo()">add todo</button>
  </div>
</template>

<script>
export default {
  name: "addTodo",
  props: {
    todos: {
      type: Array,
      required: true,
    }
  },
  data() {
    return {
      todoModel: "",
    };
  },
  methods: {
    addTodo() {
      if (this.todoModel != "") {
        this.todos.push({
          text: this.todoModel,
          isComplete: this.isDone,
        });
      }
    },
  },
};
</script>

<style>
</style>