<template>
  <ul class="collection">
    <TodoItem
      v-for="(todo, index) of todos"
      v-bind:key="todo.id"
      v-bind:todo="todo"
      v-bind:index="index"
      v-on:remove-todo="removeTodo"
    />
  </ul>
</template>

<script>
import TodoItem from "@/components/TodoItem";

export default {
  props: ["todos"],
  components: { TodoItem },
  methods: {
    removeTodo(id) {
      this.$emit("remove-todo", id);
    }
  }
};
</script>

<style scoped></style>
