<script setup>
import { useUserStore } from "./stores/users";
import { ref } from "vue";
const user_store = useUserStore();

const user_input = ref({
  name: "",
  email: "",
});

const sort = ref(false);

const CreateUser = () => {
  user_store.create(user_input.value);
  user_input.value = {
    name: "",
    email: "",
  };
};
</script>

<template>
  <form action="" @submit.prevent="CreateUser">
    <input type="text" v-model="user_input.name">
    <input type="text" v-model="user_input.email">
    <input type="submit" value="submit">
  </form>
  <div v-for="user in user_store.users">{{ user }}</div>
</template>

<style scoped></style>
