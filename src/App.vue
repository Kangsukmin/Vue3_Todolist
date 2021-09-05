<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput @addTodo="addTodo"></TodoInput>
    <TodoList :propsdata="state.todoItems" @removeTodo="removeTodo"></TodoList>
    <TodoFooter @removeAll="removeAll"></TodoFooter>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";
import TodoHeader from "./components/TodoPage/TodoHeader.vue";
import TodoInput from "./components/TodoPage/TodoInput.vue";
import TodoList from "./components/TodoPage/TodoList.vue";
import TodoFooter from "./components/TodoPage/TodoFooter.vue";

export default defineComponent({
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter,
  },
  setup() {
    interface iState {
      todoItems: string[];
    }

    const state: iState = reactive({
      todoItems: [],
    });

    const addTodo = (inputValue: string) => {
      if (inputValue !== "") {
        const value: string = inputValue && inputValue.trim();
        localStorage.setItem(value, value);
        state.todoItems.push(value);
      }
    };

    const removeTodo = (todoItem: string, index: number) => {
      localStorage.removeItem(todoItem);
      state.todoItems.splice(index, 1);
    };

    const removeAll = () => {
      localStorage.clear();
      state.todoItems = [];
    };

    // Created
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        state.todoItems.push(localStorage.key(i) as string);
      }
    }

    return {
      state,
      addTodo,
      removeTodo,
      removeAll,
    };
  },
});
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f8;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
