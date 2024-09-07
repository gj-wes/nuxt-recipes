<script setup lang="ts">
import type { Recipe } from '~/types/types';

const route = useRoute();
const { data:recipe, error } = await useFetch<Recipe>(`https://dummyjson.com/recipes/${route.params.id}`);

</script>

<template>
  <div v-if="error" class="text-red-600 font-semibold text-lg">
    {{ error.message }}
  </div>
  <div v-else-if="recipe" class="bg-white shadow-lg rounded-lg overflow-hidden">
      <img :src="recipe.image" :alt="recipe.name" class="w-full h-64 object-cover">
      <div class="p-6">
        <h1 class="text-3xl font-bold text-gray-800 mb-4">{{ recipe.name }}</h1>
        
        <div class="flex flex-wrap gap-2 mb-4">
          <span v-for="tag in recipe.tags" :key="tag" class="bg-blue-100 text-blue-800 text-xs font-semibold px-2.5 py-0.5 rounded">
            {{ tag }}
          </span>
        </div>
        
        <div class="grid grid-cols-2 sm:grid-cols-4 gap-4 mb-6">
          <div class="text-center">
            <p class="text-gray-600 text-sm">Prep Time</p>
            <p class="font-semibold">{{ recipe.prepTimeMinutes }} mins</p>
          </div>
          <div class="text-center">
            <p class="text-gray-600 text-sm">Cook Time</p>
            <p class="font-semibold">{{ recipe.cookTimeMinutes }} mins</p>
          </div>
          <div class="text-center">
            <p class="text-gray-600 text-sm">Servings</p>
            <p class="font-semibold">{{ recipe.servings }}</p>
          </div>
          <div class="text-center">
            <p class="text-gray-600 text-sm">Calories</p>
            <p class="font-semibold">{{ recipe.caloriesPerServing }} / serving</p>
          </div>
        </div>
        
        <div class="mb-6">
          <h2 class="text-2xl font-semibold text-gray-800 mb-2">Ingredients</h2>
          <ul class="list-disc list-inside space-y-2">
            <li v-for="ingredient in recipe.ingredients" :key="ingredient" class="text-gray-700">
              {{ ingredient }}
            </li>
          </ul>
        </div>
        
        <div class="mb-6">
          <h2 class="text-2xl font-semibold text-gray-800 mb-2">Instructions</h2>
          <ol class="list-decimal list-inside space-y-4">
            <li v-for="(step, index) in recipe.instructions" :key="index" class="text-gray-700">
              {{ step }}
            </li>
          </ol>
        </div>
        
        <div class="flex justify-between items-center">
          <div>
            <span class="text-yellow-400">★</span>
            <span class="ml-1 text-gray-600">{{ recipe.rating }} ({{ recipe.reviewCount }} reviews)</span>
          </div>
          <div>
            <span class="bg-green-100 text-green-800 text-sm font-medium px-2.5 py-0.5 rounded">
              {{ recipe.difficulty }}
            </span>
            <span class="ml-2 bg-purple-100 text-purple-800 text-sm font-medium px-2.5 py-0.5 rounded">
              {{ recipe.cuisine }}
            </span>
          </div>
        </div>
      </div>
    </div>
    <div v-else class="text-center text-gray-600 text-lg">
      Loading...
    </div>
</template>
