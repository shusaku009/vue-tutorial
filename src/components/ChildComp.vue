<script setup>
const props = defineProps({
  msg: String,
  test: String,
});
const email = defineEmits(["response"]);

email("response", "Hello from child");
</script>

<template>
  <div>
    <h1>Child Component</h1>
    <h2>{{ msg || "No props passed yet" }}</h2>
    <h2>{{ test || "No props passed yet" }}</h2>
    <h2>{{ childMsg || "No child msg yet" }}</h2>
  </div>
</template>
