<script setup lang="ts">
import type { Recipe } from '~/types/types';
const props = defineProps<{
  recipe?: Recipe
}>();
</script>

<template>
  <div class="bg-white rounded-lg shadow-md overflow-hidden hover:shadow-lg transition-shadow duration-300 ease-in-out p-5">
    <h2 class="text-xl font-semibold text-gray-800 mb-2">{{ recipe.name }}</h2>
    <div class="flex justify-between items-center mb-4">
      <span class="bg-blue-100 text-blue-800 text-sm font-medium px-2.5 py-0.5 rounded">
        {{ recipe.cuisine }}
      </span>
      <span class="bg-green-100 text-green-800 text-sm font-medium px-2.5 py-0.5 rounded">
        Difficulty: {{ recipe.difficulty }}
      </span>
    </div>
    <NuxtLink 
      :to="`/recipe/${recipe.id}`"
      class="inline-block bg-indigo-600 text-white text-sm font-medium py-2 px-4 rounded hover:bg-indigo-700 transition-colors duration-300 ease-in-out"
    >
      Read More
    </NuxtLink>
  </div>
</template>
