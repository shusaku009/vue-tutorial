<script setup lang="ts">
import { reactive, ref } from "vue";

const counter = reactive({ count: 0 });
const count = ref(0);
const message = ref("Hello World!");
const titleClass = ref("title");

function incrementCount() {
  count.value++;
}
</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is: {{ counter.count }}</p>
  <h1 :class="titleClass">Make me red</h1>
  <button @click="incrementCount()">countUp</button>
  {{ count }}
</template>

<style>
.title {
  color: red;
}
</style>
