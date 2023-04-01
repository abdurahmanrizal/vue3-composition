<template>
  <div>Name: {{ name }}</div>
  <div>Age: {{ age }}</div>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
  setup() {
    const user = reactive({
      name: "Abdurahman",
      age: 25,
    });

    setTimeout(() => ((user.name = "Jack"), (user.age = 30)), 2000);

    return { ...toRefs(user) };
  },
};
</script>

<style></style>
