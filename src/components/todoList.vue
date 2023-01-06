<template>
  <div class="container">
    <ul class="list-group">
      <small class="text-danger" v-if="todoItems.length === 0"
        >Empty list please add a todo</small
      >
      <li class="list-group-item" v-for="todoItem in todoItems" :key="todoItem">
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
  watch: {
    todoItems: {
      handler() {
        localStorage.setItem("todoItems", JSON.stringify(this.todoItems));
      },
      deep: true,
    },
  },
};
</script>
