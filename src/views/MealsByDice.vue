<script setup>
import dice from "../assets/dice.svg";
import Meals from "../components/Meals.vue";
import axiosClient from "../axiosClient.js";
import { ref } from "vue";

const meals = ref([]);
const disable = ref(false);

const randomMeal = () => {
  axiosClient
    .get(`random.php`)
    .then(({ data }) => meals.value.push(data.meals[0]));
};
</script>
<template>
  <div class="p-8 text-center pb-4">
    <h1 class="text-4xl font-bold mb-4 text-sky-500">Meals by Dice</h1>
    <div>
      <button
        :disabled="meals.length == 6"
        @click="randomMeal"
        class="hover:scale-90 transition-all"
      >
        <img :src="dice" />
      </button>
      <p class="my-4 font-semibold text-red-600" v-if="meals.length == 6">
        Only 6 meals allowed
      </p>
      <Meals :meals="meals" />
    </div>
  </div>
</template>
