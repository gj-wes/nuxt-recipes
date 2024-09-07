<script setup lang="ts"></script>
<template>
  <nav class="bg-gray-800 mb-4">
    <div class="mx-auto container px-2 sm:px-6 lg:px-8 flex h-16 items-center">
      <div class="flex flex-1 items-center justify-start space-x-4">
        <div class="flex flex-shrink-0 items-center">
          <img class="h-8 w-auto" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500" alt="Your Company">
        </div>
        <div class="flex space-x-4">
          <NuxtLink to="/" class="rounded-md px-3 py-2 text-sm font-medium text-gray-300" activeClass="bg-gray-900 text-white">Home</NuxtLink>
          <NuxtLink to="/recipes" class="rounded-md px-3 py-2 text-sm font-medium text-gray-300" activeClass="bg-gray-900 text-white">Recipies</NuxtLink>
        </div>
      </div>
    </div>
  </nav>
  <main>
    <div class="container mx-auto px-4">
      <slot />
    </div>
  </main>
</template>
