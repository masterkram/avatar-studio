<template>
  <div class="bg-gray-900 h-screen px-10 py-12">
    <h1 class="font-extrabold text-transparent text-8xl bg-clip-text bg-gradient-to-r from-purple-400 to-pink-600">
      Mark's Avatar Studio
    </h1>
    <div class="border-b border-gray-800 my-4"></div>
    <NuxtPage />
  </div>
</template>

<script setup lang="ts">
interface Avatar {
  name: string,
  url: string | null,
}

const avatars: Avatar[] = [{ name: "Leonard Krasner", url: null }];

const people = [
  {
    name: 'Leonard Krasner',
    imageUrl:
      'https://images.unsplash.com/photo-1519345182560-3f2917c472ef?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=8&w=1024&h=1024&q=80',
  },
  // More people...
]
</script>

<style lang="postcss">
body {
  @apply bg-gray-900
}
</style>