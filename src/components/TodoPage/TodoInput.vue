<template>
  <div class="inputBox shadow">
    <input
      v-model="state.newTodoItem"
      type="text"
      placeholder="Type what you have to do"
      @keyup.enter="addTodo"
    />
    <q-btn class="addContainer" color="primary" icon="add" @click="addTodo" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";

export default defineComponent({
  setup(_, { emit }) {
    const state = reactive({
      newTodoItem: "",
    });

    const addTodo = () => {
      emit("addTodo", state.newTodoItem);
      clearInput();
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

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  height: 50px;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>
