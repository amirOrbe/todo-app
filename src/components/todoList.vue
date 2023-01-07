<template>
  <div class="container">
    <ul class="list-group">
      <small class="text-danger" v-if="computedArray.length === 0"
        >Empty list please add a todo</small
      >
      <li
        class="list-group-item"
        v-for="todoItem in computedArray"
        :key="todoItem"
      >
        <div class="row">
          <div class="col-sm">
            <span class="text-dark">{{ todoItem.id }}</span>
          </div>
          <div class="col-sm mb-0">
            <p
              :class="[
                todoItem.done ? 'text-decoration-line-through' : '',
                'text-break',
              ]"
            >
              {{ todoItem.task }}
            </p>
          </div>
          <div class="col-sm">
            <input v-model="todoItem.done" type="checkbox" />
            <label class="form-check-label text-muted"> Mark as Done </label>
          </div>
          <div class="col-sm">
            <button
              @click="deleteTodoItem(todoItem)"
              class="btn btn-outline-secondary"
            >
              Delete
            </button>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    todoItems: [],
  },
  computed: {
    computedArray() {
      return this.todoItems;
    },
  },
  watch: {
    todoItems: {
      handler() {
        localStorage.setItem("todoItems", JSON.stringify(this.todoItems));
      },
      deep: true,
    },
  },
  methods: {
    deleteTodoItem(todoItem) {
      const newList = this.todoItems.filter((item) => item !== todoItem);
      console.log(newList);
    },
  },
};
</script>
