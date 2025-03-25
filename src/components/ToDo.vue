<script>
import { ToDo, Toolbar } from "@dhx/trial-todolist";
import "@dhx/trial-todolist/dist/todo.css";

export default {
  props: ["tasks", "users", "projects"],

  mounted() {
    this.todo = new ToDo(this.$refs.todo_container, {
      users: this.users,
      tasks: this.tasks,
      projects: this.projects,
      // other configuration properties
    });

    this.toolbar = new Toolbar(this.$refs.toolbar_container, {
      api: this.todo.api,
      // other configuration properties
    });
  },

  unmounted() {
    this.todo.destructor();
    this.toolbar.destructor();
  }
};
</script>

<template>
  <div class="component_container">
    <div ref="toolbar_container"></div>
    <div ref="todo_container" class="widget"></div>
  </div>
</template>
