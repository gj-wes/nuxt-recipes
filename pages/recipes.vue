<script setup lang="ts">
import type { RecipeResponse } from '~/types';
const { data, error } = useFetch<RecipeResponse>('https://dummyjson.com/recipes?limit=12');
</script>

<template>
  <div v-if="error">
    {{ error.message }}
  </div>
  <div v-else-if="data" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
    <RecipeListItem 
      v-for="recipe in data.recipes" 
      :key="recipe.id"
      :recipe="recipe"
    />
  </div>
  <div v-else>
    Loading...
  </div>
</template>
