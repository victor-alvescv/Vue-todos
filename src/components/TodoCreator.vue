<script setup>
import { defineEmits, reactive } from "vue";
import TodoButton from '../components/TodoButton.vue'

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
  todo: "",
  invalid: null,
  errMsg: "",
});

const createTodo = () => {
  todoState.invalid = null
  if (todoState.todo !== "") {
    emit("create-todo", todoState.todo)
    todoState.todo = "";
    return
  }
  todoState.invalid = true;
  todoState.errMsg = "Todo value cannot be empty"
};
</script>

<template>
  <div class="input-wrap" :class="{ 'input-err' : todoState.invalid }">
    <input v-model="todoState.todo" type="text" />
    <TodoButton @click="createTodo()" />
  </div>
  <!-- <p v-if="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</p> || v-if does not show the element inside the structure -->
  <p v-show="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</p> <!--  v-show just set the line to a display:none -->
</template>

<style lang="scss" scoped>
.input-wrap {
  display: flex;
  transition: 250ms ease;
  border: 1px solid gray;
  border-radius: 1px;


  &.input-err {
    border-color: red;
  }

  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }

  input {
    width: 100%;
    padding: 8px 6px;
    border: none;
    background-color: black;
    color: rgba(255, 255, 255, 0.774);
    padding-left: 10px;
    &:focus {
      outline: none;
    }
  }
}

.err-msg {
  margin-top: 6px;
  font-size: 12px;
  text-align: center;
  color: red;
}
</style>
