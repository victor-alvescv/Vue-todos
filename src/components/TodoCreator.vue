<script setup>
import { defineEmits, reactive } from "vue";
import TodoButton from "../components/TodoButton.vue";

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
  todo: "",
  invalid: null,
  errMsg: "",
});

const createTodo = () => {
  todoState.invalid = null;
  if (todoState.todo !== "") {
    emit("create-todo", todoState.todo);
    todoState.todo = "";
    return;
  }
  todoState.invalid = true;
  todoState.errMsg = "Todo value cannot be empty";
};
</script>

<template>
  <div class="input--wrapper">
  <div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
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
        d="M12 10.5v6m3-3H9m4.06-7.19-2.12-2.12a1.5 1.5 0 0 0-1.061-.44H4.5A2.25 2.25 0 0 0 2.25 6v12a2.25 2.25 0 0 0 2.25 2.25h15A2.25 2.25 0 0 0 21.75 18V9a2.25 2.25 0 0 0-2.25-2.25h-5.379a1.5 1.5 0 0 1-1.06-.44Z"
      />
    </svg>

    <input
      placeholder="Work Tomorrow at 12:30pm..."
      v-model="todoState.todo"
      type="text"
    />
  </div>
  <TodoButton @click="createTodo()" />
</div>
  <!-- <p v-if="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</p> || v-if does not show the element inside the structure -->
  <p v-show="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</p>
  <!--  v-show just set the line to a display:none -->
</template>

<style lang="scss" scoped>
.input--wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
}

.input-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  transition: all 300ms ease;
  border: 1px solid hsla(0, 0%, 100%, 0.14);
  border-radius: 6px;
  background-color: #0a0a0a;
  overflow-x: hidden;
  font-family: "Inter";
  justify-content: center;
  align-items: center;
  overflow-y: hidden;
  height: 40px;

  &:hover {
    border-color: hsla(0, 0%, 100%, 0.247);
  }

  &:focus-within {
    border-color: hsla(0, 0%, 100%, 0.425);
  }

  &.input-err {
    border-color: red;
  }

  svg {
    width: 20px;
    color: hsla(0, 0%, 100%, 0.14);
    color: #888888;
    margin-left: 10px;
  }

  input {
    width: 500px;
    padding: 12px 6px;
    border: none;
    font-size: 12px;
    font-weight: 500;
    background-color: #0a0a0a;
    color: #a1a1a1;
    padding-left: 10px;
    &:focus {
      outline: none;
    }
  }
  ::placeholder {
    color: #888888;
  }
}

.err-msg {
  margin-top: 6px;
  font-size: 12px;
  text-align: center;
  color: red;
  font-family: "Inter";
  font-weight: 500;
}
</style>
