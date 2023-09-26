<template>
  <div>
    <span class="relative inline-block">
      <img class="h-16 w-16 rounded-full" :src="url" alt="" />
      <span class="absolute right-0 top-0 block h-4 w-4 rounded-full bg-green-400 ring-2 ring-white" />
    </span>
  </div>
</template>

<script setup>
defineProps(['url']);
</script>