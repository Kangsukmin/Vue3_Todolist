<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
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
    return {};
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
