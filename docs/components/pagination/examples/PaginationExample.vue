<template>
  <div class="vp-raw flex flex-col">
    <Pagination @goToPage="ici($event)" :currentPage="currentPage"></Pagination>
  </div>
  {{ currentPage }}
</template>
<script setup>
import { Pagination } from '../../../../src/index'
import { ref } from 'vue'

const currentPage = ref(1)

const ici = (p) => {
  currentPage.value = p
  alert(currentPage.value)
}
</script>
