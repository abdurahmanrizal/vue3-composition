<template>
  <UserComponent
    :label="label"
    :user="user"
    class="active"
    data-id="23"
    @submit="onSubmit">
    <template v-slot:belowContent="{ data }">
      <div>{{ data }}</div>
    </template>
    <div>Ini slot</div>
  </UserComponent>
  <button @click="onChangeUser">Change</button>
</template>

<script>
import { onMounted, reactive, ref } from "vue";
import UserComponent from "./components/UserComponent.vue";
export default {
  components: { UserComponent },
  setup() {
    const label = ref("biodata");
    const user = reactive({
      name: "Abdurahman",
      age: 25,
    });

    const onChangeUser = () => {
      user.name = "Jack";
    };
    const onSubmit = (value) => {
      console.log(value);
    };

    return { label, user, onChangeUser, onSubmit };
  },
};
</script>

<style></style>
