<script setup>
const { meal } = defineProps({
  meal: {
    required: true,
    type: Object,
  },
});

const truncateWords = (str, count) => {
  if (!str) return str;
  return str.split(" ").slice(0, count).join(" ");
};
</script>
<template>
  <div class="bg-white shadow rounded-xl hover:scale-105 transition-all">
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img
        :src="meal.strMealThumb"
        :alt="meal.strMeal"
        class="rounded-t-xl w-full h-48 object-cover"
      />
    </router-link>
    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="mb-4">
        {{ truncateWords(meal.strInstructions, 20) }}
      </p>
      <div class="flex items-center justify-between">
        <a
          target="_blank"
          class="px-3 py-2 rounded border-2 text-white border-sky-600 bg-sky-500 hover:bg-sky-600 transition-colors"
          :href="meal.strYoutube"
          >Check Video</a
        >
      </div>
    </div>
  </div>
</template>
