<template>
  <div id="app">
    <h1>My TODO App!</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",
  components: {
    TodoList
  }
};
</script>

<style>
#app {
  margin: 0 auto;
}
</style>
