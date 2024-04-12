<script setup>
defineProps({
  image: String,
  title: String,
  description: String
})
</script>

<template>
  <div class="mb-3 cursor-pointer rounded-xl hover:bg-slate-100">
    <div class="flex items-center gap-3 py-2 px-3">
      <img :src="image" class="w-[48px] rounded-full">
      <div>
        <h3 class="font-black text-lg">{{ title }}</h3>
        <div class="text-sm text-gray-500">{{ description }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
