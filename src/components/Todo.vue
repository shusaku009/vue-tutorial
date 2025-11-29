<script setup></script>

<template>
  <div>
    <h1>Todo</h1>
  </div>
  <div>
    <h2>Todo List</h2>
    <h3>InComplete</h3>
    <ul>
      <li>Todo 1</li>
      <li>Todo 2</li>
      <li>Todo 3</li>
    </ul>
  </div>
  <div>
    <h3>Complete</h3>
    <ul>
      <li>Todo 1</li>
      <li>Todo 2</li>
      <li>Todo 3</li>
    </ul>
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
