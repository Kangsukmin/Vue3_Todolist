<template>
  <section>
    <ul>
      <li
        v-for="(todoItem, index) in state.todoItem"
        :key="todoItem"
        class="shadow"
      >
        <i class="checkBtn fas fa-check" aria-hidden="true" />
        {{ todoItem }}
        <span
          class="removeBtn"
          type="button"
          @click="removeTodo(todoItem, index)"
        >
          <i class="far fa-trash-alt" aria-hidden="true" />
        </span>
      </li>
    </ul>
  </section>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";

export default defineComponent({
  setup() {
    interface iState {
      todoItem: string[];
    }

    const state: iState = reactive({
      todoItem: [],
    });

    // Created
    if (localStorage.length > 0) {
      for (let i = 0; i < localStorage.length; i++) {
        state.todoItem.push(localStorage.key(i) as string);
      }
    }

    const removeTodo = (todoItem, index) => {
      localStorage.removeItem(todoItem);
      state.todoItem.splice(index, 1);
    };

    return {
      state,
      removeTodo,
    };
  },
});
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}

.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}

.removeBtn {
  margin-left: auto;
  color: #de4343;
}
</style>
