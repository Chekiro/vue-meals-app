<template>
  <header class="bg-slate-400 shadow h-16 flex justify-between items-stretch">
    <router-link
      :to="{ name: 'home' }"
      class="inline-flex items-center font-semibold px-2 h-full transition-colors hover:bg-sky-500 hover:text-white ml-2"
    >
      Home
    </router-link>
    <div class="flex items-center gap-1">
      <router-link
        :to="{ name: 'byName' }"
        class="inline-flex items-center font-semibold px-2 h-full transition-colors hover:bg-sky-500 hover:text-white"
      >
        Search Meals
      </router-link>
      <router-link
        :to="{ name: 'byLetter' }"
        class="inline-flex items-center font-semibold px-2 h-full transition-colors hover:bg-sky-500 hover:text-white"
      >
        Meals By Letter
      </router-link>
      <router-link
        :to="{ name: 'ingredients' }"
        class="inline-flex items-center font-semibold px-2 h-full transition-colors hover:bg-sky-500 hover:text-white"
      >
        Meals By Ingredients
      </router-link>
      <router-link
        :to="{ name: 'byDice' }"
        class="inline-flex items-center font-semibold px-2 h-full transition-colors hover:bg-sky-500 hover:text-white"
      >
        Meals By Dice
      </router-link>
    </div>
  </header>
</template>
