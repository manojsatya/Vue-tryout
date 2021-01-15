<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/Layout/Header";
import AddTodo from "./components/AddTodo";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    AddTodo,
    Todos,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((res) => (this.todos = res.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0px;
  margin: 0px;
}
</style>
