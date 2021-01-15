<template>
  <div class="todoitem" v-bind:class="{ 'is-complete': todo.completed }">
    <p>
      <input type="checkbox" v-on:change="markComplete" />

      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)">Delete</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "Todoitem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todoitem {
  background-color: #f4f4f4;
  padding: 10px;
  border-bottom: 1px blue solid;
}

.is-complete {
  text-decoration: line-through;
}
</style>
