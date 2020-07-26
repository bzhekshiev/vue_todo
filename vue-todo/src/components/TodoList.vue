<template>
  <div>
    <ul class="collection">
      <TodoItem
        v-for="todo of todos"
        v-bind:todo="todo"
        v-bind:key="todo.id"
        v-on:remove-todo="removeTodo"
      />
    </ul>
    <div class="todoitem__detail">
      <span>All tasks: {{todos.length}}</span>
      <span>Done: {{doneTasks.length}}</span>
    </div>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem";

export default {
  props: ["todos"],
  components: { TodoItem },
  methods: {
    removeTodo(id) {
      this.$emit("remove-todo", id);
    },
  },
  computed: {
    doneTasks() {
      return this.todos.filter((todo) => todo.completed === true);
    },
  },
};
</script>

<style scoped>
.todoitem__detail {
  display: flex;
  justify-content: space-around;
}
</style>
