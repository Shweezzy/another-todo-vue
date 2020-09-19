<template>
  <div id="app">
    <h1 class="title">{{ title }}</h1>
    <div class="todoList">
      <input
        class="inputText"
        type="text"
        v-model="todoModel"
        placeholder="type todo..."
        @keyup.enter="addTodo"
      />
      <button @click="addTodo">add todo</button>
      <p></p>
      <todo-list :todos="todos" @removeTodo="removeTodo" />
      <hr />
      <todo-total :todos="todos" style="float: right" />
    </div>
  </div>
</template>

<script>
import todoList from "./components/todoList";
import todoTotal from "./components/todoTotal";

export default {
  name: "App",
  components: {
    todoList,
    todoTotal,
  },
  data() {
    return {
      title: "Todo app",
      todoModel: "",
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
    addTodo() {
      if (this.todoModel != "") {
        this.todos.push({
          text: this.todoModel,
          isComplete: this.isDone,
        });
        localStorage.setItem("todos", JSON.stringify(this.todos));
      }
      this.todoModel = "";
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
  },
};
</script>

<style>
.title {
  text-align: center;
  font-family: "Century Gothic", sans-serif;
}
.todoList {
  width: 97.5%;
  height: 100%;
  padding: 1em;
  outline: 1px solid black;
  min-height: 300px;
}
.todoId {
  color: rgb(0, 0, 0);
  font-weight: bold;
}
.modelCheck {
  display: inline-block;
  float: right;
  transform: scale(1.59);
  margin-top: 3.7px;
}
span:first-letter {
  color: red;
}
.isComplete {
  color: green;
  text-decoration: line-through;
}
.inputText {
  width: 80%;
  margin-left: 5%;
}
@media only screen and (max-width: 600px) {
  .inputText {
    width: 50%;
  }
  .todoList {
    width: 90%;
  }
}
</style>
