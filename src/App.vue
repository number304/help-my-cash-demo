<template>
  <div class="flex justify-center items-center h-screen">
    <UserInfoCard
      v-if="user"
      :profile-pic="user.profilePic"
      :username="user.username"
      :location="user.location"
      :status="user.status"
    />
  </div>
</template>

<script setup lang="ts">
import axios from "axios";
import { onMounted, ref } from "vue";
import UserInfoCard from "./components/UserInfoCard.vue";
import User from "./models/user.model";

const user = ref<User>();

onMounted(async () => {
  await axios.get("https://rickandmortyapi.com/api/character/1").then((res) => {
    user.value = {
      username: res.data.name,
      location: res.data.location.name,
      profilePic: res.data.image,
      status: res.data.status,
    };
  });
});
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
