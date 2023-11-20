<template>
  <section
    class="lg:h-[300px] shadow-lg rounded-lg bg-slate-400 grid lg:grid-cols-2 pb-2 lg:pb-0"
  >
    <img
      v-if="profilePic"
      :src="profilePic"
      :alt="`User ${username} Profile Picture`"
      class="profile-pic"
    />

    <article class="p-2 lg:p-4 text-white flex flex-col justify-center">
      <h1
        class="font-bold text-2xl text-white hover:text-black transition-colors mb-2"
      >
        {{ username }}
      </h1>

      <p class="font-medium text-lg">Location:</p>
      <p class="ml-2 mt-1">{{ location }}</p>

      <p class="font-medium mt-4 text-lg">Last seen:</p>
      <p class="ml-2 mt-1">13, June 2023</p>

      <p class="font-medium mt-4 text-lg">Status:</p>

      <div class="flex items-center ml-2 mt-1 space-x-2">
        <span
          class="rounded-full w-5 h-5 block"
          :class="status === 'Alive' ? 'bg-green-400' : 'bg-yellow-300'"
        ></span>
        <p>{{ translateStatus(status) }}</p>
      </div>
    </article>
  </section>
</template>

<script setup lang="ts">
import User from "../models/user.model";

defineProps<User>();

function translateStatus(status: string) {
  if (status === "Alive") return "Connected";
  return status;
}
</script>

<style>
.profile-pic {
  @apply w-[200px] h-[200px] lg:w-[300px] lg:h-[300px] rounded-lg rounded-b-none lg:rounded-none lg:rounded-l-lg;
}
</style>
