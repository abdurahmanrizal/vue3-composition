<template>
  <div>Count {{ nilai }}</div>
  <button @click="add">Add</button>
</template>

<script>
import { reactive, ref, toRefs, watch, watchEffect } from "vue";
export default {
  setup() {
    const count = reactive({
      nilai: 0,
      foo: "bar",
    });

    const num1 = ref(1);
    const num2 = ref(2);
    const add = () => {
      //   count.nilai++;
      num1.value++;
      num2.value++;
    };

    // watchEffect(
    //   () => {
    //     console.log(count.nilai);
    //   },
    //   {
    //     flush: "post",
    //     onTrack(e) {
    //       console.log(e);
    //     },
    //   }
    // );

    // watch untuk memantau ref
    // watch(num1, (after, before) => {
    //   console.log(num1.value);
    //   console.log(after);
    //   console.log(before);
    // });

    // watch untuk memantau salah satunya object reactive
    // watch(
    //   () => count.nilai,
    //   (after, before) => {
    //     console.log(count.nilai);
    //     console.log(after);
    //     console.log(before);
    //   }
    // );

    // watch untuk memantau lebih dari satu ref
    watch([num1, num2], (current, before) => {
      console.log(current);
    });
    return { ...toRefs(count), add };
  },
};
</script>

<style></style>
