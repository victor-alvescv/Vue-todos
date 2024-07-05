<script setup>
import { ref, watch, computed } from "vue";
import { uid } from "uid";
import { Icon } from "@iconify/vue";
import TodoCreator from "../components/TodoCreator.vue";
import TodoItem from "../components/TodoItem.vue";
const todoList = ref([]);

watch(
  todoList,
  () => {
    setTodoListLocalStorage();
  },
  {
    deep: true,
  }
);

const todoCompleted = computed(() => {
  return todoList.value.every((todo) => todo.isCompleted);
});

const fetchTodoList = () => {
  const savedTodoList = JSON.parse(localStorage.getItem("todoList"));
  if (savedTodoList) {
    todoList.value = savedTodoList;
  }
};

fetchTodoList();

const setTodoListLocalStorage = () => {
  localStorage.setItem("todoList", JSON.stringify(todoList.value));
};

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null,
  });
};

const toggleTodoComplete = (todoPos) => {
  // Todo Position
  todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
};

const toggleEditTodo = (todoPos) => {
  todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
};

const updateTodo = (todoVal, todoPos) => {
  todoList.value[todoPos].todo = todoVal;
};

const deleteTodo = (todoId) => {
  todoList.value = todoList.value.filter((todo) => todo.id !== todoId);
};
</script>

<template>
  <main>
    <div class="title--wrapper"></div>
    <TodoCreator @create-todo="createTodo" />
    <!--  listens the emit create-todo from the TodoCreator.vue component -->
    <ul v-if="todoList.length > 0" class="todo-list">
      <TodoItem
        v-for="(todo, index) in todoList"
        :todo="todo"
        :index="index"
        @toggle-complete="toggleTodoComplete"
        @edit-todo="toggleEditTodo"
        @update-todo="updateTodo"
        @delete-todo="deleteTodo"
      />
      <!-- :todo="todo" is used to pass props to a child component, ":" is shorthand for v-bind, "todo" here is a prop that is being
       passed to the TodoItem component, and the value of this prop is the current "todo" object from the todoList array -->
      <!--  For each item in the todoList, teh v-for directive creates a new instance of the TodoItem component, the "todo variable represents the current item in the iteration" -->
    </ul>
    <p v-else class="todos-msg">
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
          d="M12 9.75v6.75m0 0-3-3m3 3 3-3m-8.25 6a4.5 4.5 0 0 1-1.41-8.775 5.25 5.25 0 0 1 10.233-2.33 3 3 0 0 1 3.758 3.848A3.752 3.752 0 0 1 18 19.5H6.75Z"
        />
      </svg>

      <span>Todo List is empty...</span>
    </p>
    <p v-if="todoCompleted && todoList.length > 0" class="todos-msg">
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
          d="m20.25 7.5-.625 10.632a2.25 2.25 0 0 1-2.247 2.118H6.622a2.25 2.25 0 0 1-2.247-2.118L3.75 7.5M10 11.25h4M3.375 7.5h17.25c.621 0 1.125-.504 1.125-1.125v-1.5c0-.621-.504-1.125-1.125-1.125H3.375c-.621 0-1.125.504-1.125 1.125v1.5c0 .621.504 1.125 1.125 1.125Z"
        />
      </svg>

      <span>No remaining Todos...</span>
    </p>
  </main>
</template>

<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 700px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  .title--wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    margin-bottom: 20px;
  }
  h1 {
    text-align: center;
    font-weight: 900;
    color: rgba(255, 255, 255, 0.925);
  }
  svg {
    color: #ededed;
    width: 30px;
  }
  .todo-list {
    display: flex;
    list-style: none;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    margin-top: 32px;
    gap: 20px;
  }

  .todos-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    gap: 8px;
    color: #ededed;
    margin-top: 100px;

    svg {
      width: 50px;
      color: hsla(0, 0%, 100%, 0.14);
    }

    span {
      font-size: 14px;
      font-weight: 500;
      color: #888888;
    }
  }
}
</style>
