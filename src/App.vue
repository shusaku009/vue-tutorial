<script setup lang="ts">
import { reactive, ref, computed, onMounted } from "vue";

let id = 0;

const counter = reactive({ count: 0 });
const count = ref(0);
const message = ref("Hello World!");
const titleClass = ref("title");
const text = ref("");
const modeltext = ref("");
const awesome = ref(true);
const newTodo = ref("");
const hideCompleted = ref(false);
const todos = ref([
  { id: id++, text: "Learn HTML" },
  { id: id++, text: "Learn JavaScript" },
  { id: id++, text: "Learn Vue" },
]);
const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((todo) => !todo.done)
    : todos.value;
});
const pElementRef = ref(null);

function incrementCount() {
  count.value++;
}

function onInput(e: Event) {
  const target = e.target as HTMLInputElement;
  if (!target) return;
  text.value = target.value;
}

function toggleAwesome(): void {
  awesome.value = !awesome.value;
}

function addTodo(): void {
  todos.value.push({ id: id++, text: newTodo.value });
  newTodo.value = "";
}

function removeTodo(todo): void {
  todos.value = todos.value.filter((t) => t !== todo);
}

onMounted(() => {
  pElementRef.value.textContent = "mounted";
});
</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is: {{ counter.count }}</p>
  <h1 :class="titleClass">Make me red</h1>
  <button @click="incrementCount()">countUp</button>
  {{ count }}
  <div><input :value="text" @input="onInput" placeholder="Type here" /></div>
  <p>{{ text }}</p>
  <div><input type="text" v-model="modeltext" placeholder="Type here" /></div>
  <p>{{ modeltext }}</p>
  <button @click="toggleAwesome">Toggle</button>
  <h1>{{ awesome ? "Awesome" : "Not Awesome" }}</h1>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Vue is not awesome!</h1>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo" />
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? "Show Completed" : "Hide Completed" }}
  </button>
  <p ref="pElementRef">Hello World</p>
</template>

<style>
.title {
  color: red;
}
.done {
  text-decoration: line-through;
}
</style>
