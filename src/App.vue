<template>
  <div id="app">
    <h1 class="title">{{ title }}</h1>
    <div class="todoList">
      <input class="inputText" type="text" v-model="todoModel" placeholder="type todo..." />
      <button @click="addTodo(id++)">add todo</button>
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
      id: 0,
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
          id: this.id,
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
}
.todoList {
  width: 98%;
  height: 100%;
  padding: 1em;
  outline: 1px solid black;
  min-height: 300px;
}
.todoId {
  color: rgb(0, 0, 0);
  font-weight: bold;
}
#todoText {
  font-size: 18px;
  text-transform: capitalize;
}
.modelCheck {
  display: inline-block;
  margin-left: 1em;
}
.todoText {
  text-transform: capitalize;
  font-size: 1.5em;
}
.deleteTodo {
  height: 20px;
}
.isComplete {
  color: green;
  text-decoration: line-through;
}
.todoId {
  font-size: 1.5em;
}
.inputText {
  width: 80%;
  margin-left: 5%;
}
</style>
