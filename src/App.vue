<template>
  <h1>Todo List</h1>

  <todo-new @add-new-todo="addNewTodo"></todo-new>

  <article v-for="todo of todos" :key="todo.id">
    <input type="checkbox" v-model="todo.done" :id="todo.id" />
    <label :for="todo.id">{{ todo.label }}</label>
  </article>

  {{ doneCount }} tâches réalisées sur {{ todos.length }} au total.

  <button v-on:click="removeDoneTodos">Retirer les todos effectuées</button>
</template>

<script>
import TodoNew from "./components/todo-new";
export default {
  name: "App",
  components: {
    TodoNew,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          label: "Manger",
          done: true,
        },
        {
          id: 2,
          label: "Dormir",
          done: false,
        },
      ],
    };
  },
  methods: {
    addNewTodo(newTodoName) {
      this.todos.push({
        id: Date.now(),
        label: newTodoName,
        done: false,
      });
    },
    removeDoneTodos() {
      this.todos = this.todos.filter((todo) => !todo.done);
    },
  },
  computed: {
    doneCount() {
      return this.todos.filter((todo) => todo.done).length;
    },
  },
};
</script>

<style></style>
