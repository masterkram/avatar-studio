<template>
  <div class="grid grid-cols-6 my-5 gap-3 text-gray-100 font-medium uppercase">
    <NuxtLink v-for="cat in Object.keys(data['categories'])" :to="cat">
      <Card>
        {{ cat }}
      </Card>
    </NuxtLink>
  </div>
</template>

<script setup lang="ts">
const d = ['humanoid', 'animal', 'fantasy', 'robotic', 'sci-fi', 'historical', 'mystery', 'superheros', 'mythological', 'fairy tale', 'fantasy', 'zodiac', 'social media', 'communication', 'productivity', 'developer', 'e-commerce', 'gaming', 'streaming', 'food', 'meme']
const categories = await queryContent('/avatars').findOne();

const { data, pending, error } = await useAsyncData('categories', () => queryContent('/avatars').findOne(), { pick: ['categories'] }
);
</script>