<template>
  <div id="app">
    <h1 class="title">{{ title }}</h1>
    <todo-list />
  </div>
</template>

<script>
import todoList from "./components/todoList";

export default {
  name: "App",
  components: {
    todoList,
  },
  data() {
    return {
      title: "Todo app",
    };
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
    width: 70%;
  }
  .todoList {
    width: 90%;
  }
}
</style>
