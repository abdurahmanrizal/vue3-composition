<template>
  <div>{{ message }}</div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    // pengenalan ref
    const message = ref("halo");
    setTimeout(() => (message.value = "Composition API"), 2000);
    return { message };
  },
};
</script>

<style></style>
