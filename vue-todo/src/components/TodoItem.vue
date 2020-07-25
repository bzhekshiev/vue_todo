<template>
  <li class="todoitem collection-item valign-wrapper left-align">
    <label class="todoitem__input" v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed=!todo.completed" :checked="todo.completed === true" />
      <span>
        <strong>{{todo.id}}</strong>
        {{todo.title}}
      </span>
    </label>
    <i class="small material-icons rm_btn" v-on:click="$emit('remove-todo', todo.id)">delete_forever</i>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  components: {}
};
</script>

<style scoped>
.todoitem {
  justify-content: space-between;
  cursor: pointer;
}
.todoitem__input {
  width: 95%;
  cursor: pointer;
}
.todoitem:hover {
  background: #eee;
  transition-delay: 0.2s;
}
.rm_btn {
  color: #a82323;
  cursor: pointer;
}
.done {
  color: wheat;
}
</style>