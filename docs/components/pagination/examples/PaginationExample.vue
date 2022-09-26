<template>
  <div class="vp-raw flex flex-col">
    <Pagination @goToPage="ici" :currentPage="currentPage"></Pagination>
  </div>
</template>
<script setup>
import { Pagination } from '../../../../src/index'
import { ref } from 'vue'

const currentPage = ref(1)

const ici = (p) => {
  currentPage.value = p
}
</script>
