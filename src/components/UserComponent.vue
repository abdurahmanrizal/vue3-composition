<template>
  <div>{{ label }} - {{ user.name }}</div>
  <slot></slot>
  <div>{{ description }}</div>
  <slot name="belowContent" :data="title"></slot>
  <button @click="onSubmit">Submit</button>
</template>

<script>
import { computed, onMounted, ref, toRefs } from "vue";
export default {
  props: {
    label: {
      type: String,
      default: "",
    },
    user: {
      type: Object,
      default: () => {},
    },
  },
  setup(props, { attrs, slots, emit }) {
    const { label, user } = toRefs(props);
    const title = ref("ini judul");
    const description = computed(() => {
      return `${label.value} - ${user.value.name}`;
    });
    onMounted(() => {
      console.log(attrs);
      console.log(slots);
    });
    const onSubmit = () => {
      emit("submit", "ini adalah submit dari user component");
    };

    function showHello() {
      console.log("hello world");
    }

    return { description, title, onSubmit, showHello };
  },
};
</script>

<style></style>
