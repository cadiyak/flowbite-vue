<script setup>
import { computed } from 'vue'

const props = defineProps({
  columns: Array,
})

const nbrColumn = computed(() => 'grid-cols-' + (props.columns.length + 1))

</script>

<template>
        <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
          <tr>
            <th v-for="column in columns" scope="col" class="px-6 py-3">{{ column.label }}</th>
<!--            <th scope="col" class="px-6 py-3">Actions</th>-->
          </tr>
        </thead>
</template>