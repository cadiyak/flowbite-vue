<script setup>
import { computed, ref } from 'vue'

const props = defineProps({
  data: Object,
  columns: Array,
  striped: {
    type: Boolean,
    default: false,
  },
  hoverable: {
    type: Boolean,
    default: false,
  },
})

const columns = ref(props.columns)
const stripedClass = ref('bg-white dark:bg-gray-900 dark:border-gray-700')
const NotStripedClass = ref('bg-gray-50 dark:bg-gray-800 dark:border-gray-700')

const headerColumns = computed(() => {
  return columns.value.filter((column) => {
    if (column.head === true) {
      return (
          column
      )
    }
  })
})

const normalColumns = computed(() => {
  return columns.value.filter((column) => {
    if (column.head === false) {
      return (
          column
      )
    }
  })
})

const paginate = (array, page_size, page_number) => {
    return array.slice((page_number - 1) * page_size, page_number * page_size)
}
paginate(props.data, 1, props.data.length)

const isStriped = (index) => {
  if (props.striped && index%2 === 0) {
    return true
  }
}

const isLast = (index) => {
  if (props.data.length - 1 === index) {
    return true
  }
}

const dataLength = () => {
  return props.data.value.length
}
</script>

<template>
        <tbody>
          <tr v-for="(datum, index) in data" :key="datum"
                :class="[
                    isStriped(index) ? stripedClass : NotStripedClass,
                    {'hover:bg-gray-50 dark:hover:bg-gray-600' : hoverable},
                    {'border-b' : !isLast(index)},
                ]"
          >
            <th v-for="column in headerColumns" :key="column" scope="row"
                class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white"
            >
              {{ datum[column.field] }}
            </th>
            <td v-for="column in normalColumns" :key="column" class="px-6 py-4">
              {{ datum[column.field] }}
            </td>
          </tr>
        </tbody>
</template>
