<template>
  <div id="app">
    <div class="section">
      <div class="container">
        <TodoComp :todos="todos" @addTodo="addTodo" @complete="complete" @deleteTodo="deleteTodo" />
      </div>
    </div>
  </div>
</template>

<script>
import TodoComp from "./components/TodoComp";
export default {
  name: "App",
  components: {
    TodoComp
  },

  data() {
    return {
      name: "subroto",
      todos: [
        {
          userId: 1,
          id: 1,
          title: "delectus aut autem",
          completed: false
        },
        {
          userId: 1,
          id: 2,
          title: "quis ut nam facilis et officia qui",
          completed: false
        },
        {
          userId: 1,
          id: 3,
          title: "fugiat veniam minus",
          completed: false
        },
        {
          userId: 1,
          id: 4,
          title: "et porro tempora",
          completed: true
        }
      ]
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.unshift(todo);
    },
    complete(id) {
      const updated_todos = this.todos.map(todo =>
        todo.id == id ? Object.assign(todo, { completed: true }) : todo
      );

      this.todos = updated_todos;
    },
    deleteTodo(id) {
      let deleted_todos = this.todos.filter(todo => todo.id != id);
      this.todos = deleted_todos;
    }
  }
};
</script>

<style>
#app {
  perspective: 1000px;
  min-height: 100vh;
  background-color: #f8961e;
  font-family: "roboto";
}
</style>