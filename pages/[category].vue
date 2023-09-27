<template>
  <div>
    <div class="text-white inline-flex flex-wrap gap-5 items-center">
      <NuxtLink to="/"><button class="font-medium border rounded p-2">Exit</button></NuxtLink>
      <h2 class="text-md sm:text-xl md:text-2xl uppercase font-bold">Avatars > {{ category }}</h2>
    </div>
    <p class="text-gray-200 italic mt-8 mb-1">tip: try clicking a card.</p>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-3">
      <Card @click="() => copySign(avatar)" v-for="avatar in avatars"
        class="flex flex-col items-center py-5 bg-gray-800 border border-gray-700 hover:bg-gradient-to-bl hover:from-gray-800 hover:to-blue-600 transition-all rounded">
        <Avatar :url="avatar.url" />
        <span class="text-white font-medium">{{ avatar.name }}</span>
        <span :class="avatar.copied.value ? 'opacity-100' : 'opacity-0'"
          class="text-sm text-gray-300 font-medium transition-all duration-500">copied to clipboard :)</span>
      </Card>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Avatar {
  name: string,
  url: string,
  copied: Ref<boolean>,
}

const config = useRuntimeConfig();
const router = useRouter();
const route = useRoute();
const category = route.params.category as string;
const data = await queryContent('/avatars').findOne()
const avatars: Avatar[] = data["categories"][category].map((element: any) => { return { ...element, copied: ref(false) } })

function copySign(avatar: Avatar) {
  const url = `${config.public.baseUrl}${avatar.url}`;
  navigator.clipboard.writeText(url).catch().then(() => {
    avatar.copied.value = true;
    setInterval(() => avatar.copied.value = false, 1000)
  });
}

onMounted(() => {
  document.onkeyup = function (e) {
    if (e.key == 'Escape') {
      router.replace('/');
    }
  };
});
</script>