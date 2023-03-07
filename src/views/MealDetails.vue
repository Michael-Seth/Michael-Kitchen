<template>
  <div class="bg-white py-6 sm:py-8 lg:py-12">
    <div class="mx-auto max-w-screen-xl px-4 md:px-8">
      <div class="grid gap-8 md:grid-cols-2 lg:gap-12 ">
        <div class=" lg:flex lg:flex-col lg:justify-center">
          <p class="text-center font-bold text-green-500 md:text-left">{{ meal.strArea }} {{ meal.strCategory }} </p>

          <h1 class="mb-4 text-center text-2xl font-bold text-gray-800 sm:text-3xl md:mb-6 md:text-left">{{ meal.strMeal
          }}</h1>
          <p class="my-4 font-bold text-2xl text-gray-800">Recipe</p>
          <p class="mb-6 text-gray-700 text-justify text-base md:mb-8">{{ meal.strInstructions }}</p>
        </div>
        <div>
          <div class="h-auto overflow-hidden rounded-lg bg-gray-100 shadow-lg">
            <img :src="meal.strMealThumb" :alt="meal.strMeal" class="h-full w-full object-cover object-center" />
          </div>
        </div>
        <div class="md:col-span-2">


          <div class="flex text-[1rem] justify-between">
            <a :href="meal.strYoutube" target="_blank"
              class="group bg-red-600 text-white py-4 px-6 rounded-[5px] font-semibold hover:bg-white hover:border-red-600 hover:text-red-600 hover:border-2">
              <span>▷</span>
              <span class="ml-3">Watch Tutorial</span>
            </a>

          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router';
import axiosClient from '../axiosClient';

const route = useRoute();
const meal = ref({})

onMounted(() => {
  axiosClient.get(`lookup.php?i=${route.params.id}`)
    .then(({ data }) => {
      meal.value = data.meals[0] || {}
    })
})

</script>