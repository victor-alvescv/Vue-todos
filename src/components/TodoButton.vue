<script setup></script>

<template>
  <button>
    <slot>Create</slot>
  </button>
</template>

<style lang="scss" scoped>
button {
  padding: 8px 16px;
  border: none;
  background-color: black;
  color: rgba(255, 255, 255, 0.925);
  border-left: 1px solid gray;
}
</style>
