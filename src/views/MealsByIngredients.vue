<script setup>
import { onMounted, ref, computed } from "vue";
import { useRoute } from "vue-router";
import store from "../store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const ingredient = computed(() => store.state.ingredient);
const meals = computed(() => store.state.mealsByIngredient);

onMounted(() => {
  store.dispatch("searchMealsByIngredient", route.params.ingredient);
});
</script>
<template>
  <div class="p-8 pb-0 text-center">
    <h1 class="text-4xl font-bold mb-4 text-sky-500">
      Meals for {{ ingredient.strIngredient }}
    </h1>
  </div>

  <Meals :meals="meals" />
</template>
