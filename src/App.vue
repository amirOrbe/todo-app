<template>
  <nav id="nav" class="navbar navbar-light bg-dark">
    <a class="navbar-brand text-white px-3" href="/">
      <img
        src="../src/assets/logo.png"
        width="50"
        height="50"
        class="d-inline-block align-center"
        alt=""
      />
      Todo List
    </a>
    <div class="px-3">
      <button class="btn btn-outline-light">Sign in</button>
    </div>
  </nav>
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
        @keyup.enter="addTodoItem"
      />
      <div v-if="newTodoItem">
        <button
          class="btn btn-outline-secondary"
          type="button"
          id="button-add-todo-item"
          @click="addTodoItem"
        >
          Add
        </button>
      </div>
    </div>
  </div>
  <todoList v-bind:todoItems="todoItems" />
</template>

<script>
import { ref } from "vue";
import todoList from "./components/todoList.vue";

export default {
  name: "App",
  components: {
    todoList,
  },
  setup() {
    const newTodoItem = ref("");
    return {
      newTodoItem,
    };
  },
  data() {
    return {
      todoItems: [],
    };
  },
  methods: {
    addTodoItem() {
      this.todoItems.push({
        id: this.todoItems.length + 1,
        task: this.newTodoItem,
        done: false,
      });
      this.newTodoItem = "";
    },
  },
  mounted() {
    if (localStorage.getItem("todoItems")) {
      this.todoItems = JSON.parse(localStorage.getItem("todoItems"));
    }
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
