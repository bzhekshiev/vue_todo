<template>
  <div id="app">
    <div class="container">
      <Input v-on:add-todo ="AddTodoItem"/>
      <TodoList v-bind:todos="todos" v-on:remove-todo="removeTodo" />
    </div>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import Input from "@/components/Input";
import M from "materialize-css";
export default {
  data() {
    return {
      todos: [
        { id: 1, title: "task 1", completed: false },
        { id: 2, title: "task 2", completed: false },
        { id: 3, title: "task 3", completed: false }
      ]
    };
  },
  components: {
    TodoList,
    Input
  },
  methods:{
    removeTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    AddTodoItem(todo){
      this.todos.push(todo)
    }
  },
  mounted() {
    M.AutoInit();
  }
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
