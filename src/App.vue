<script setup lang="ts">
import { useStore } from "./store/store";
import Other from "./components/Other.vue";

const store = useStore();

const unsubscribe = store.$subscribe((_, state) => {
  console.log("1");
  if (state.counter === 2) {
    unsubscribe();
  }
});

const handleClick = () => {
  store.$patch({
    counter: store.counter + 1,
  });
  // Or
  // store.$patch((state) => {
  //   state.counter++;
  // });
};
</script>

<template>
  <div>{{ store.counter }}</div>
  <button @click="handleClick()">Click Me!</button>

  <hr>
  <Other />
</template>

<style>
* {
  padding: 0;
  margin: 0;
}

div {
  padding: 50px;
}
</style>
