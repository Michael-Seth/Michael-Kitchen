<template>
  <div class="grid grid-cols-1 md:grid-cols-4 gap-2 px-2">
    <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
  </div>
  <div v-if="!meals.length" class="flex justify-center text-gray-600 p-8">
    <loading />
  </div>
</template>

<script setup>
import MealItem from './MealItem.vue';
import Loading from './Loading.vue';

const { meals } = defineProps({
  meals: {
    required: true,
    type: Array,
  }
})

</script>
