<template>
  <div>
    <navbar></navbar>

    <main>Vous êtes sur l'accueil !</main>

    <br />

    <h1>To-do List</h1>
    <input name="todo" v-model="todoInput" @keydown.enter="addItem" /><br />
    <ul>
      <li v-for="todo in todos" :key="todo.id" :class="{ done: todo.done }">
        {{ todo.value }}
        <input type="checkbox" v-model="todo.done" />
      </li>
    </ul>
  </div>
</template>

<script>
import navbar from "../components/navbar.vue";

/*
{
  id: Date.now(),
  value: "",
  done: false
}
*/

export default {
  data() {
    return {
      todoInput: "",

      todos: [
        {
          id: 1,
          value: "un item",
          done: false,
        },
        {
          id: 2,
          value: "deux items",
          done: false,
        },
      ],
    };
  },
  methods: {
    addItem() {
      if (this.todoInput.length === 0) return;
      this.todos.push({
        id: Date.now(),
        value: this.todoInput,
        done: false,
      });
      this.todoInput = "";
    },
  },
};
</script>

<style scoped>
.done {
  text-decoration: line-through;
  color: red;
}
</style>
