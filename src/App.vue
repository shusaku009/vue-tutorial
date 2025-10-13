<script setup lang="ts">
import { reactive, ref } from "vue";

const counter = reactive({ count: 0 });
const count = ref(0);
const message = ref("Hello World!");
const titleClass = ref("title");
const text = ref("");

function incrementCount() {
  count.value++;
}

function onInput(e: Event) {
  const target = e.target as HTMLInputElement;
  if (!target) return;
  text.value = target.value;
}
</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is: {{ counter.count }}</p>
  <h1 :class="titleClass">Make me red</h1>
  <button @click="incrementCount()">countUp</button>
  {{ count }}
  <div><input :value="text" @input="onInput" placeholder="Type here" /></div>
  {{ text }}
</template>

<style>
.title {
  color: red;
}
</style>
