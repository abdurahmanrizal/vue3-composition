<template>
  <div>Count : {{ counter }}</div>
  <br />
  <button @click="add">Add</button>
  <div>Result {{ result }}</div>
</template>

<script>
import { reactive, ref, toRefs, computed } from "vue";
export default {
  setup() {
    // dengan menggunakan ref
    // const counter = ref(0);
    // dengan menggunakan reactive
    const counter = reactive({
      counter: 0,
    });

    const addNum = ref(1);
    // tidak menggunakan setter dan getter
    // const result = computed(() => counter.counter + addNum.value);
    // menggunakan setter dan getter
    const result = computed({
      get: () => counter.counter + addNum.value,
      set: (val) => (addNum.value = val),
    });

    const add = () => {
      result.value = 5;
      counter.counter++;
    };
    return { ...toRefs(counter), add, result };
  },
};
</script>

<style></style>
