<template>
  <div class="card">
    <h3>{{ item.title }}</h3>
    <p>Type: {{ item.type }}</p>
    <p>Price: ${{ item.price }}</p>
    <p>Stock: {{ item.stock }}</p>
    <p>Status: {{ item.isOnline ? 'Online' : 'Offline' }}</p>
  </div>
</template>

<script lang="ts">
import type { Item } from '~/data/mockItems'

export default {
  props: {
    item: {
      type: Object as () => Item,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
.card {
  padding: 16px;
  border-radius: 8px;
  background: #f5f5f5;
}
</style>
