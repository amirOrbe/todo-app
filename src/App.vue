<script setup>
import { ref } from "vue";
const newTodoItem = ref("");
const todo = ref([]);
const addTodoItem = () => {
  todo.value.push({
    id: todo.value.length + 1,
    task: newTodoItem.value,
    done: false,
  });
  newTodoItem.value = "";
};
</script>

<template>
  <div class="container p-3">
    <h1 class="display-3">Welcome to your Todo List</h1>

    <div class="input-group mb-3">
      <input
        v-model="newTodoItem"
        type="text"
        class="form-control"
        placeholder="Add a todo"
        aria-label="Todo input"
        aria-describedby="Todo input"
      />
      <div v-if="newTodoItem">
        <button
          class="btn btn-outline-secondary"
          type="button"
          id="button-add-todo-item"
          v-on:click="addTodoItem"
        >
          Add
        </button>
      </div>
    </div>
  </div>
  <todoList :todoItems="todo" />
</template>

<script>
import todoList from "./components/todoList.vue";

export default {
  name: "App",
  components: {
    todoList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
