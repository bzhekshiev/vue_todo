<template>
  <form v-on:submit.prevent="onSubmit" class="row valign-wrapper">
    <div class="input-field col s10">
      <input id="task__input" type="text" class="validate" v-model="title" />
      <label for="task__input">Task</label>
    </div>
    <button class="btn waves-effect waves-light col s2" type="submit" name="action">
      Create
      <i class="material-icons right">send</i>
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ""
    };
  },
  components: {},
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodoItem = {
          id: new Date(),
          title: this.title,
          completed: false
        };
        this.$emit("add-todo", newTodoItem);
        this.title = "";
      }
    }
  }
};
</script>

<style scoped>
</style>