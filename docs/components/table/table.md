<script setup>
import TableDefaultExample from './examples/TableDefaultExample.vue';
import TableHoverExample from './examples/TableHoverExample.vue';
import TableStripedExample from './examples/TableStripedExample.vue';
</script>
# Table

## Default table

<TableDefaultExample />

```vue
<script setup>
import { Table } from 'flowbite-vue'
</script>

<template>
  <div class="vp-raw flex flex-col">
    <Table></Table>
  </div>
</template>
```

## Props - striped

<TableStripedExample />

```vue
<script setup>
import { Table } from 'flowbite-vue'
</script>

<template>
  <div class="vp-raw flex flex-col">
    <Table :striped="true"></Table>
  </div>
</template>
```

## Props - hover

<TableHoverExample />

```vue
<script setup>
import { Table } from 'flowbite-vue'
</script>

<template>
  <div class="vp-raw flex flex-col">
    <Table :hoverable="true"></Table>
  </div>
</template>
```
