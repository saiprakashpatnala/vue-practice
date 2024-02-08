<script setup>
const { data, removeTask } = defineProps(["data", "removeTask"]);

</script>

<template>
  <li v-for="(item, index) in data" :key="index">
    <p>{{ item }}</p>
    <button @click="removeTask(index)">Remove</button>
  </li>
</template>