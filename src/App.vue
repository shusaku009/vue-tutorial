<script setup lang="ts">
import { reactive, ref } from "vue";

const counter = reactive({ count: 0 });
const count = ref(0);
const message = ref("Hello World!");
const titleClass = ref("title");
const text = ref("");
const modeltext = ref("");
const awesome = ref(true);

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
</template>

<style>
.title {
  color: red;
}
</style>
