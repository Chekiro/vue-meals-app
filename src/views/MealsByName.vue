<script setup>
import { useRoute } from "vue-router";
import { onMounted, ref } from "vue";
import { computed } from "@vue/reactivity";
import store from "../store";
import Meals from "../components/Meals.vue";

const keyword = ref("");
const route = useRoute();
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  if (keyword.value) {
    store.dispatch("searchMeals", keyword.value);
  } else {
    store.commit("setSearchedMeals", []);
  }
}

onMounted(() => {
  keyword.value = route.params.name;
  if (keyword.value) {
    searchMeals();
  }
});
</script>
<template>
  <div class="p-8 pb-0 text-center">
    <h1 class="text-4xl font-bold mb-4 text-sky-400">Search Meals by Name</h1>
  </div>
  <div class="px-8 pb-3">
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 bg-white border-gray-200 focus:ring-sky-500 focus:border-sky-500 w-full"
      placeholder="Search for Meals"
      @change="searchMeals"
    />
  </div>
  <Meals :meals="meals" />
</template>
