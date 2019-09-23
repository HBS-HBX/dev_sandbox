<template>
  <div class="todo-list">
    <NewTodo v-model="newTodoText" placeholder="New todo" @keydown.enter="addTodo" />
    <ul v-if="todos.length">
      <TodoListItem v-for="todo in todos" :key="todo.id" :todo="todo" @remove="removeTodo"></TodoListItem>
    </ul>
  </div>
</template>

<script>
import NewTodo from "./NewTodo";
import TodoListItem from "./TodoListItem";
let nextTodoId = 1;

export default {
  components: {
    NewTodo,
    TodoListItem
  },
  data: () => ({
    newTodoText: "",
    todos: [
      {
        id: nextTodoId++,
        text: "First"
      },
      {
        id: nextTodoId++,
        text: "Second"
      },
      {
        id: nextTodoId++,
        text: "Third"
      }
    ]
  }),
  methods: {
    removeTodo(idToRemove) {
      this.todos = this.todos.filter(todo => {
        return todo.id !== idToRemove;
      });
    },
    addTodo() {
      const trimmedText = this.newTodoText.trim();
      if (trimmedText) {
        this.todos.push({ id: nextTodoId++, text: trimmedText });
        this.newTodoText = "";
      }
    }
  }
};
</script>
