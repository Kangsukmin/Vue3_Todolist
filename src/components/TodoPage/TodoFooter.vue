<template>
  <div class="clearAllContainer">
    <span class="clearAllBtn" @click="clearAll">Clear All</span>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  setup() {
    const clearAll = () => {
      localStorage.clear();
    };
    return {
      clearAll,
    };
  },
});
</script>

<style scoped>
.clearAllContainer {
  width: 8.5rem;
  height: 50px;
  line-height: 50px;
  background-color: white;
  border-radius: 5px;
  margin: 0 auto;
}

.clearAllBtn {
  color: #e20303;
  display: black;
}
</style>
