<template>
  <Header />

  <Meals :meals="meals" />
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import Header from "../components/Header.vue"
import Meals from "../components/Meals.vue";
import axiosClient from "../axiosClient.js";

const meals = ref([]);

onMounted(async () => {
  const requests = [];

  for (let i = 0; i < 8; i++) {
    requests.push(axiosClient.get("random.php"));
  }

  const responses = await Promise.all(requests);

  meals.value = responses.map((response) => response.data.meals[0]);
});

</script>
