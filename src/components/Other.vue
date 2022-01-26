<script setup lang="ts">
import { useStore } from "../store/store";

const store = useStore();

store.$subscribe(() => {
  console.log("2");
});
</script>

<template>
  <div>{{ store.counter }}</div>
</template>
