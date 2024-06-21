<script>
import { ToDo, Toolbar } from "@dhx/trial-todolist";
import "@dhx/trial-todolist/dist/todo.css";

export default {
  props: ["tasks", "users", "projects"],

  mounted() {
    const todo = new ToDo(this.$refs.todo_container, {
      users: this.users,
      tasks: this.tasks,
      projects: this.projects,
    });

    new Toolbar(this.$refs.toolbar_container, {
      api: todo.api
    });
  },
  unmounted() {
    this.$refs.toolbar_container.innerHTML = "";
    this.$refs.todo_container.innerHTML = "";
  }
};
</script>

<template>
  <div ref="toolbar_container"></div>
  <div ref="todo_container" style="width: 100%; height: 100%"></div>
</template>
