<template>
  <nav aria-label="Page navigation example">
    <ul class="inline-flex -space-x-px">
      <li>
        <a href="#" class="py-2 px-3 ml-0 leading-tight text-gray-500 bg-white rounded-l-lg border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">
          Previous
        </a>
      </li>
      <li v-for="(page, index) in totalPages" @click="$emit('goToPage', pageNumber(index)), goToPage(index)" key="index">
        <a v-if="pageNumber(index) !== currentPage"  href="#" class="py-2 px-3 leading-tight text-gray-500 bg-white border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">
          {{ pageNumber(index) }}
        </a>
        <a v-else href="#" aria-current="page" class="py-2 px-3 text-blue-600 bg-blue-50 border border-gray-300 hover:bg-blue-100 hover:text-blue-700 dark:border-gray-700 dark:bg-gray-700 dark:text-white">
          {{ pageNumber(index) }}
        </a>
      </li>
      <li>
        <a href="#" class="py-2 px-3 leading-tight text-gray-500 bg-white rounded-r-lg border border-gray-300 hover:bg-gray-100 hover:text-gray-700 dark:bg-gray-800 dark:border-gray-700 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-white">
          Next
        </a>
      </li>
    </ul>
  </nav>
</template>
<script lang="ts" setup>
import {computed, ref, toRefs } from 'vue'
import type { PropType } from 'vue'

const props = defineProps({
  currentPage: {
    type: Number,
    default: 1,
  },
  layout: {
    type: String, // 'navigation' | 'pagination' | 'table'
    default: 'pagination',
  },
  showIcons: {
    type: Boolean,
    default: false,
  },
  totalPages: {
    type: Number,
    default: 5,
  },
})

const pageNumber = (index: number) => {
  return index + 1
}

const currentPage = ref(props.currentPage)

const goToPage = (index: number) => {
  currentPage.value = pageNumber(index)
}

</script>
