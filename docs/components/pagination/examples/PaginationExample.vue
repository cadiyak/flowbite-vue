<template>
  <div class="vp-raw flex flex-col">
    <Pagination @goToPage="goToPage($event)" @goToPreviousPage="goToPreviousPage" @goToNextPage="goToNextPage" :currentPage="currentPage" :totalPages="totalPages"></Pagination>
  </div>
</template>
<script setup>
import { Pagination } from '../../../../src/index'
import { ref } from 'vue'

const currentPage = ref(1)
const totalPages = 6

const goToPage = (p) => {
  currentPage.value = p
}

const goToPreviousPage = () => {
  if (currentPage.value > 1) {
    currentPage.value --
  }
}
const goToNextPage = () => {
  if (currentPage.value < totalPages) {
    currentPage.value ++
  }
}

</script>
