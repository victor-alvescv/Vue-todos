<script setup>
import { RouterView } from "vue-router";
import TodoHeader from "./components/TodoHeader.vue";

</script>

<template>
  <TodoHeader />
  <RouterView />
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&family=Nunito+Sans:ital,opsz,wght@0,6..12,200..1000;1,6..12,200..1000&display=swap');
* {
  font-family: "Inter";
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-weight: 700;
  letter-spacing: 1px;
}

body {
  background-color: black;
}

.container {
  max-width: 1100px;
  margin: 0 auto;
  background-color: #0a0a0a;
  color: #EDEDED;
}
</style>
