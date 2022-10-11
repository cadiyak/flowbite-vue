<script lang="ts" setup>
// const props = defineProps({
//   className: {
//     type: String,
//     default: '',
//   },
// })

import TableHead from './TableHead.vue'
import TableBody from './TableBody.vue'
import {ref} from 'vue'

const props = defineProps({
  data: {
    type: Array,
    default() {
      return [
        {
          'name': 'Apple MacBook Pro 17"',
          'color': 'Sliver',
          'category': 'Laptop',
          'price': '$2999',
        },
        {
          'name': 'Microsoft Surface Pro',
          'color': 'White',
          'category': 'Laptop PC',
          'price': '$1999',
        },
        {
          'name': 'Magic Mouse 2',
          'color': 'Black',
          'category': 'Accessories',
          'price': '$99',
        },
      ]
    },
  },
  columns: {
    type: Array,
    default() {
      return [
        {
          label: 'Product name ',
          field: 'name',
          head: true,
        },
        {
          label: 'Color',
          field: 'color',
          head: false,
        },
        {
          label: 'Category',
          field: 'category',
          head: false,
        },
        {
          label: 'Price',
          field: 'price',
          head: false,
        },
      ]
    },
  },
  striped: {
    type: Boolean,
    default: false,
  },
  hoverable: {
    type: Boolean,
    default: false,
  },
  pagination: {
    type: Object,
    default() {
      return {
        perPage: 1,
      }
    },
  },
})

const data = ref(props.data)
const columns = ref(props.columns)

const dataLength = () => {
  return data.value.length
}

</script>

<template>
  <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
    <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
      <TableHead :columns="columns"/>
      <TableBody :data="data" :columns="columns" :striped="striped" :hoverable="hoverable"/>
    </table>
  </div>
</template>
