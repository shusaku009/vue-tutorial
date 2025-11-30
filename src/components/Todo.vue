<script setup>
import { ref } from "vue";

let id = 1;

const newTodo = ref("");
const todos = ref([]);

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false });
  console.log(todos.value);
  newTodo.value = "";
}
</script>

<template>
  <div>
    <h1>Todo</h1>
  </div>
  <div class="todo-list-container">
    <h2>Todo List</h2>
    <div>
      <h3>New Todo</h3>
      <form @submit.prevent="addTodo">
        <input v-model="newTodo" required placeholder="new todo" />
        <button>追加</button>
      </form>
    </div>
    <div class="todo-list">
      <h3>InComplete</h3>
      <ul class="todo-list-item">
        <li v-for="todo in todos" key="todo.id">
          <input type="checkbox" />
          <span>{{ todo.text }}</span>
          <button>X</button>
        </li>
      </ul>
    </div>
    <div class="todo-list">
      <h3>Complete</h3>
      <ul class="todo-list-item">
        <li>Todo 1</li>
        <li>Todo 2</li>
        <li>Todo 3</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.todo-list-container {
  border: 1px solid #ccc;
  background-color: #f0f0f0;
  padding: 2% 10%;
  margin: 5% auto;
  width: 50%;
}
.todo-list-item {
  list-style: none;
  padding: 5px;
  margin: 5px;
}
</style>
