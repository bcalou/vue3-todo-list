<template>
  <form @submit.prevent="addNewTodo">
    <label for="newTodo">Nouvelle todo</label>
    <input id="newTodo" required v-model="newTodoName" />
    <button>Ajouter</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTodoName: "",
    };
  },
  methods: {
    addNewTodo() {
      this.$emit("addNewTodo", this.newTodoName);
      this.newTodoName = "";
    },
  },
};
</script>
