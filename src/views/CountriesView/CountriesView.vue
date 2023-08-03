<script setup>
import { ref, reactive, onMounted } from 'vue'
import SingleCountryView from '../../components/singleCountryView.vue'

let countryList = reactive([])
let isLoading = ref(true)
const search = ref("")

onMounted(() => {
  let url = 'https://restcountries.com/v3.1/all'
  fetch(url)
    .then((res) => res.json())
    .then((data) => {
      countryList = data
      isLoading.value = false
      console.log(countryList)
    })
    .catch((error) => console.error('Error Occure', error))
})

const getAllCountrySearch = () => {
    return countryList.filter((country) => {
        return country.name.common.toLowerCase().startsWith(search.value.toLowerCase())
    })
}

</script>

<template>
  <section class="bg-gray-200 w-full h-full pb-5">
    <div class="container mx-auto">
      <input
        v-model="search"
        class="w-full mt-5 p-3 rounded-md focus:outline-none mb-5"
        placeholder="Searche Your Country"
        type="search"
        name=""
        id=""
      />
     
      <h1 v-if="isLoading"></h1>
      <div v-else class="grid grid-cols-5 gap-7">
        <SingleCountryView v-for="country in getAllCountrySearch()" :key="country.name" :country="country" />
      </div>
    </div>
  </section>
</template>

<style scoped></style>
