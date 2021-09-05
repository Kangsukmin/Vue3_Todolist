<template>
  <div>
    <input v-model="state.newTodoItem" type="text" />
    <button @click="addTodo">Add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";

export default defineComponent({
  setup() {
    const state = reactive({
      newTodoItem: "",
    });

    const addTodo = () => {
      if (state.newTodoItem !== "") {
        const value: string = state.newTodoItem && state.newTodoItem.trim();
        localStorage.setItem(value, value);
        clearInput();
      }
    };

    const clearInput = () => {
      state.newTodoItem = "";
    };
    return {
      state,
      addTodo,
    };
  },
});
</script>

<style scoped></style>
