<template>
  <div>
    <input @keyup.enter="addItem()" class="inputText" type="text" v-model="todoModel" placeholder="type todo..." />
    <button @click="addItem()">add todo</button>
  </div>
</template>

<script>
export default {
  name: "addTodo",
  data() {
    return {
      todoModel: "",
    };
  },
  methods: {
    addItem() {
      if (this.todoModel == "") {
        alert("Please, type todo...");
      } else this.$emit("addTodo", this.todoModel);
      this.todoModel = "";
    },
  },
};
</script>

<style>
</style>