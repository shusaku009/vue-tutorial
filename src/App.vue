<script setup lang="ts">
import { reactive, ref } from "vue";

const counter = reactive({ count: 0 });
const message = ref("Hello World!");
const titleClass = ref("title");
</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is: {{ counter.count }}</p>
  <h1 :class="titleClass">Make me red</h1>
</template>

<style>
.title {
  color: red;
}
</style>
