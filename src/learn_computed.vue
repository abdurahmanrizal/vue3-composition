<template>
  <input
    type="text"
    v-model="searchProgramming"
    placeholder="Search language programming" />
  <br />
  <br />
  <div v-for="programming in filterProgrammings" :key="programming">
    {{ programming }}
  </div>
</template>

<script>
import { computed, reactive, ref } from "vue";
export default {
  setup() {
    const searchProgramming = ref("");
    const programmings = reactive(["PHP", "JS", "RUBY", "RUST", "LUA", "R"]);

    const filterProgrammings = computed(() =>
      programmings.filter((programming) =>
        programming.toLowerCase().includes(searchProgramming.value)
      )
    );
    return { programmings, filterProgrammings, searchProgramming };
  },
};
</script>

<style></style>
