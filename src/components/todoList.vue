<template>
  <div>
    <add-todo @addTodo="addTodo" />
    <div v-for="(todo, i) in todos" :key="todo.id">
      <p>
        <span class="todoId">{{ i +1 }}</span>
        <span class="todoText">
          <strong>.</strong>
          <span :class="{isComplete: todo.isComplete}">{{ todo.text }}</span>
        </span>
        <remove-todo :todos="todos" />
        <input v-model="todo.isComplete" type="checkbox" class="modelCheck" />
      </p>
    </div>
    <hr />
    <total-todos :todos="todos" style="float: right" />
  </div>
</template>

<script>

import addTodo from "./addTodo";
import totalTodos from "./totalTodos";
import removeTodo from "./removeTodo";

export default {
  name: "todoList",
  components: {
    addTodo,
    totalTodos,
    removeTodo,
  },
  data() {
    return {
      todos: [],
      isDone: false,
    };
  },
  mounted() {
    if (localStorage.getItem("todos"))
      this.todos = JSON.parse(localStorage.getItem("todos"));
  },
  watch: {
    todos: {
      handler() {
        localStorage.setItem(`todos`, JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
  methods: {
    addTodo(text) {
      if (this.todoModel != "") {
        this.todos.push({
          text: text,
          isComplete: this.isDone,
        });
      }
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
