<template>
  <div>
    <form @submit="addTodo">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add todo..."
      />
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(event) {
      event.preventDefault();
      const newTodo = {
        id: uuidv4(),
        title: this.title,
        completed: false,
      };

      //Send to parent by emit
      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
};
</script>

<style scoped>
input {
  height: 40px;
  width: 40vw;
}
button {
  height: 40px;
  width: 20vw;
}
</style>
