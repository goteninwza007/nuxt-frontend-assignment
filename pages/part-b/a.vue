<template>
  <div class="page">
    <select v-model="selectedType">
      <option value="">All</option>
      <option v-for="type in ITEM_TYPES" :key="type" :value="type">
        {{ type }}
      </option>
    </select>

    <div class="grid">
      <ItemCard
        v-for="item in filteredItems"
        :key="item.title"
        :item="item"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue'
import { ITEM_TYPES, mockItems, type ItemType } from '~/data/mockItems';

export default {
  setup() {
    const selectedType = ref<ItemType | ''>('')
    return { selectedType, ITEM_TYPES }
  },
  computed: {
    filteredItems(){
      if (!this.selectedType) return mockItems
        return mockItems.filter(item => item.type === this.selectedType)
    }
  }
}
</script>

<style scoped lang="scss">
.page {
  padding: 24px;
}

select {
  margin-bottom: 16px;
  padding: 8px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 16px;
}
</style>
