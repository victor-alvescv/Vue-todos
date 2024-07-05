<script setup></script>

<template>
  <button>
    <slot>Add New</slot>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      stroke-width="1.5"
      stroke="currentColor"
      class="size-6"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        d="m19.5 8.25-7.5 7.5-7.5-7.5"
      />
    </svg>
  </button>
</template>

<style lang="scss" scoped>
button {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 40px;
  gap: 15px;
  width: 128px;
  border: none;
  background-color: #ededed;
  color: black;
  font-weight: bold;
  border-radius: 6px;
  cursor: pointer;
  transition: all 300ms ease;

  svg {
    width: 15px;
  }

  &:hover {
    opacity: 0.9;
  }

  &:active {
    opacity: 0.7;
  }
}
</style>
