<template>

<div class="bg-white py-6 sm:py-8 lg:py-12">
  <div class="mx-auto max-w-screen-xl px-4 md:px-8">
    <div class="grid gap-8 md:grid-cols-2 lg:gap-12">
      <div class="md:pt-8 lg:flex lg:flex-col lg:justify-center">
        <p class="text-center font-bold text-green-500 md:text-left">Who we are</p>

        <h1 class="mb-4 text-center text-2xl font-bold text-gray-800 sm:text-3xl md:mb-6 md:text-left">{{ meal.strMeal }}</h1>

        <p class="mb-6 text-gray-500 sm:text-lg md:mb-8">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Possimus accusamus esse cum, praesentium laudantium enim pariatur magnam accusantium illum animi? Quos quisquam at laborum eius?</p>
      </div>
      <div>
        <div class="h-64 overflow-hidden rounded-lg bg-gray-100 shadow-lg md:h-auto">
          <img :src="meal.strMealThumb" :alt="meal.strMeal" class="h-full w-full object-cover object-center" />
        </div>
      </div>
      <div class="md:col-span-2">
        <h2 class="mb-2 text-center text-xl font-semibold text-gray-800 sm:text-2xl md:mb-4 md:text-left">About us</h2>

        <p class="mb-6 text-gray-500 sm:text-lg md:mb-8">Lorem ipsum dolor sit amet consectetur adipisicing elit. Deserunt veritatis a suscipit similique cum obcaecati maxime, fugit officia sunt. Laudantium est repellendus, necessitatibus totam, deleniti distinctio aliquid assumenda dolore voluptas molestiae perspiciatis temporibus ex ea.</p>
      </div>
    </div>
  </div>
</div>



  <div class="max-w-[800px] mx-auto p-8">
    <h1 class="text-4xl font-bold mb-5 text-orange-500">{{ meal.strMeal }}</h1>
    <img :src="meal.strMealThumb" :alt="meal.strMeal" class="max-w-[100%]">
    <div class="grid grid-cols-1 sm:grid-cols-3 text-lg py-2">
      <div>
        <strong class="font-bold">Category:</strong> {{ meal.strCategory }}
      </div>
      <div>
        <strong class="font-bold">Area:</strong> {{ meal.strArea }}
      </div>
      <div>
        <strong class="font-bold">Tags:</strong> {{ meal.strTags }}
      </div>
    </div>

    <div class="my-3">
      {{ meal.strInstructions }}
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2">
      <div>
        <h2 class="text-2xl font-semibold mb-2">Ingredients</h2>
        <ul>
          <template v-for="(el, ind) of new Array(20)">
            <li v-if="meal[`strIngredient${ind + 1}`]">
            {{ ind + 1 }}. {{ meal[`strIngredient${ind + 1}`] }}
            </li>
          </template>
        </ul>
      </div>
      <div>
        <h2 class="text-2xl font-semibold mb-2">Measures</h2>
        <ul>
          <template v-for="(el, ind) of new Array(20)">
            <li v-if="meal[`strMeasure${ind + 1}`]">
            {{ ind + 1 }}. {{ meal[`strMeasure${ind + 1}`] }}
            </li>
          </template>
        </ul>
      </div>
      <div class="mt-4">
        <YouTubeButton :href="meal.strYoutube" />
        <a
          :href="meal.strSource"
          target="_blank"
          class="ml-3 px-3 py-2 rounded border-2 border-transparent text-indigo-600 transition-colors"
        >
          View Original Source
        </a>
      </div>
    </div>


  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router';
import axiosClient from '../axiosClient';
import YouTubeButton from '../components/YouTubeButton.vue';

const route = useRoute();
const meal = ref({})

onMounted(() => {
  axiosClient.get(`lookup.php?i=${route.params.id}`)
    .then(({ data }) => {
      meal.value = data.meals[0] || {}
    })
})

</script>