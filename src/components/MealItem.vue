<template>
  <div class="mx-auto my-10 grid max-w-screen-xl gap-y-8  ">
    <div class="group cursor mx-4 overflow-hidden rounded-2xl bg-white shadow duration-200 hover:-translate-y-4">
      <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }"
        class="flex h-40 flex-col justify-between overflow-hidden">
        <img :src="meal.strMealThumb" :alt="meal.strMeal"
          class="group-hover:scale-110 h-full w-full object-cover duration-200" />
      </router-link>
      <div class="flex-1 overflow-hidden bg-white px-6 py-8">
        <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
          <h5 class="group-hover:text-green-600 mb-4 text-xl font-bold">{{ meal.strMeal }}</h5>
        </router-link>
        <p class="mb-8 text-gray-600">{{ $filters.truncateWords(meal.strInstructions, 10) }}...</p>
        <div class="flex text-[1rem] justify-between">
          <a :href="meal.strYoutube" target="_blank" class="group font-bold focus:text-indigo-600 hover:text-green-600">
            <span>▷</span>
            <span class="underline">Watch Tutorial</span>
          </a>

        </div>
      </div>
    </div>
  </div>



  <!-- <div class="bg-white shadow rounded-xl hover:scale-105 transition-all">
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t-xl w-full h-48 object-cover" />
    </router-link>
    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="mb-4">
        {{ $filters.truncateWords(meal.strInstructions, 20) }}
      </p>
      <div class="flex items-center justify-between">
        <YouTubeButton :href="meal.strYoutube" />
      </div>
    </div>
  </div> -->
</template>

<script setup>
import YouTubeButton from './YouTubeButton.vue';

const { meal } = defineProps({
  meal: {
    required: true,
    type: Object
  }
})

</script>
