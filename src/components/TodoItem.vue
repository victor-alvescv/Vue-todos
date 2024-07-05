<script setup>
import { Icon } from "@iconify/vue";

const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
  index: {
    type: Number,
    required: true,
  },
});

defineEmits(["toggle-complete", "edit-todo", "update-todo", "delete-todo"]);
</script>

<template>
  <div class="item--wrapper">
  <input
    type="checkbox"
    :checked="todo.isCompleted"
    @input="$emit('toggle-complete', index)"
  />
  <li>
    <img src="../assets/profile.jpg" alt="" />
    <div class="todo">
      <input
        v-if="todo.isEditing"
        type="text"
        :value="todo.todo"
        @input="$emit('update-todo', $event.target.value, index)"
      />
      <span v-else :class="{ 'completed-todo': todo.isCompleted }">
        {{ todo.todo }}
      </span>
      <p v-if="!todo.isEditing">todo-creation-{{ todo.id }}</p>
      <p v-else class="editing-p">todo-creation-{{ todo.id }}</p>
    </div>
    <div class="todo-actions">
      <Icon
        icon="material-symbols:check-circle-outline"
        width="22px"
        height="22px"
        style="color: rgb(34, 159, 209)"
        class="icon"
        @click="$emit('edit-todo', index)"
        v-if="todo.isEditing"
      />
      <Icon
        icon="ph:pencil"
        width="22px"
        height="22px"
        style="color: rgb(34, 159, 209)"
        class="icon"
        @click="$emit('edit-todo', index)"
        v-else
      />
      <Icon
        icon="ph:trash-light"
        width="22px"
        height="22px"
        style="color: #f95e5e"
        class="icon"
        @click="$emit('delete-todo', todo.id)"
      />
    </div>
  </li>
</div>
</template>

<style lang="scss" scoped>

.item--wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px
}

.todoItem--wrapper {
  display: center;
  justify-content: center;
  align-items: center;
}

.editing-p {
  margin-left: 7px;
}

input[type="checkbox"] {
  appearance: none;
  width: 17px;
  height: 15px;
  background-color: rgba(255, 255, 255, 0.103);
  border-radius: 50%;
  cursor: pointer;
  box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  transition: all 300ms ease;

  &:checked {
    background-color: #2dc7c7;
  }
}
li {
  display: flex;
  align-items: center;
  gap: 12px;
  border-radius: 5px;
  padding: 16px 20px;
  height: 80px;
  width: 100%;
  margin: 0 auto;
  margin-left: 0px;
  font-size: 12px;
  background-color: #0a0a0a;
  color: #ededed;
  border: 1px solid hsla(0, 0%, 100%, 0.14);
  box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1),
    0 8px 10px -6px rgb(0 0 0 / 0.1);

  span {
    font-weight: 500;
  }

  img {
    width: 20px;
    border-radius: 25px;
  }

  &:hover {
    .todo-actions {
      opacity: 1;
    }
  }

  .todo {
    flex: 1;

    p {
      color: #a1a1a1;
      font-weight: 500;
      margin-top: 5px;
      font-size: 10px;
    }

    .completed-todo {
      text-decoration: line-through;
      text-decoration-color: rgb(139, 9, 9);
      text-decoration-thickness: 2px;
    }

    input[type="text"] {
      width: 100%;
      padding: 2px 6px;
      border: 1px solid hsla(0, 0%, 100%, 0.14);
      outline: none;
      font-weight: 500;
      font-size: 12px;
      background-color: black;
      border-radius: 6px;
      color: #ededed;
      transition: all 300ms ease;

      &:hover {
        border-color: hsla(0, 0%, 100%, 0.247);
      }
    }
  }

  .todo-actions {
    display: flex;
    gap: 6px;
    opacity: 0;
    transition: 150ms ease-in-out;
    .icon {
      cursor: pointer;
      width: 20px;
      transition: all 300ms;

      &:hover {
        opacity: 0.8;
      }
    }
  }
}
</style>
