<template>
  <div class="container">
    <div class="row">
      <SelectedItems :title="'Левый верх'" :items="selectedUserItems" />
      <SelectedItems :title="'Правый верх'" :items="selectedOtherItem ? [selectedOtherItem] : []" />
    </div>
    <div class="row">
      <ItemList
        :title="'Низ слева'"
        :items="userItems"
        :selectedItems="selectedUserItems"
        @update:selectedItems="selectedUserItems = $event"
      />
      <ItemList
        :title="'Низ справа'"
        :items="otherItems"
        :selectedItems="selectedOtherItem"
        :single="true"
        @update:selectedItems="selectedOtherItem = $event"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import SelectedItems from './components/SelectedItems.vue'
import ItemList from './components/ItemList.vue'

const userItems = ref([
  { id: 1, name: 'Shoes 1' },
  { id: 2, name: 'Shoes 2' },
  { id: 3, name: 'Shoes 3' },
  { id: 4, name: 'Shoes 4' },
  { id: 5, name: 'T-shirt 1' },
  { id: 6, name: 'T-shirt 2' },
  { id: 7, name: 'T-shirt 3' },
  { id: 8, name: 'T-shirt 4' }
])

const otherItems = ref([
  { id: 11, name: 'Jacket 1' },
  { id: 12, name: 'Jacket 2' },
  { id: 13, name: 'Jacket 3' },
  { id: 14, name: 'Jacket 4' },
  { id: 15, name: 'Hoodie 1' },
  { id: 16, name: 'Hoodie 2' },
  { id: 17, name: 'Hoodie 3' },
  { id: 18, name: 'Hoodie 4' }
])

const selectedUserItems = ref([])
const selectedOtherItem = ref(null)
</script>

<style scoped>
.container {
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 40px;
  width: 100%;
}

.row {
  display: flex;
  justify-content: space-between;
  width: 100%;
  gap: 20px;
}

.row > * {
  flex: 1;
}
</style>

