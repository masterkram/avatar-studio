<template>
  <div>
    <h2 class="text-white text-2xl uppercase font-bold">{{ category }}</h2>
    <div class="grid grid-cols-6 mt-8 gap-3">
      <Card @click="" v-for="avatar in avatars"
        class="flex flex-col items-center py-5 bg-gray-800 border border-gray-700 hover:bg-gradient-to-bl hover:from-gray-800 hover:to-blue-600 transition-all rounded">
        <Avatar :url="avatar.url" />
        <span class="text-white font-medium">{{ avatar.name }}</span>
      </Card>
    </div>
  </div>
</template>

<script setup lang="ts">
const route = useRoute();
const category = route.params.category as string;
console.log(route.params.category);
const data = await queryContent('/avatars').findOne()
const avatars = data["categories"][category];
</script>