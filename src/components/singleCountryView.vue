<script setup>
import { defineProps } from 'vue'

defineProps({
  country: Object
})
</script>

<template>
  <div class="card shadow-md bg-white p-5">
    <figure class="shadow-md">
      <img :src="country.flags.png" alt="Flag" class="w-[250px] h-[130px] mb-3 shadow-sm" />
    </figure>
    <div class="card-body">
      <h2 class="font-bold">
        <span class="text-blue-500"> {{ country.name.common }} </span>
      </h2>
      <div>
        <p class="text-xl">{{ country.status }}</p>
        <p class="text-xl">Capital: {{ country.capital}}</p>
      
      </div>
    </div>
  </div>
</template>

<style scoped></style>
