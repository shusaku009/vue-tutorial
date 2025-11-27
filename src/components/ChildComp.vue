<script setup>
const props = defineProps({
  msg: String,
});
</script>

<template>
  <div>
    <h1>Child Component</h1>
    <h2>{{ msg || "No props passed yet" }}</h2>
  </div>
</template>
