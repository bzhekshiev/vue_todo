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
    <p>All tasks: {{todos.length}}</p>
    <p>Done: {{doneTasks.length}}</p>
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

<style scoped></style>
