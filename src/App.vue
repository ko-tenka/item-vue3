<template>
  <div class="container">
    <div class="row">
      <SelectedItems :title="'Выбранные цветочки'" :items="selectedUserItems" />
      <SelectedItems :title="'Выбранная вкусняшка'" :items="selectedOtherItem ? [selectedOtherItem] : []" />
    </div>
    <div class="row">
      <ItemList
        :title="'Цветочки'"
        :items="userItems"
        :selectedItems="selectedUserItems"
        @update:selectedItems="selectedUserItems = $event"
      />
      <ItemList
        :title="'Вкуснятинка'"
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
  { id: 1, name: '🥀' },
  { id: 2, name: '🌼' },
  { id: 3, name: '🌷' },
  { id: 4, name: '🌸' },
  { id: 5, name: '🏵' },
  { id: 6, name: '🌹' },
  { id: 7, name: '🌺' },
  { id: 8, name: '🌻' }
])

const otherItems = ref([
  { id: 11, name: '🍫' },
  { id: 12, name: '🍓' },
  { id: 13, name: '🎂' },
  { id: 14, name: '🥑' },
  { id: 15, name: '🍇' },
  { id: 16, name: '🍿' },
  { id: 17, name: '🥨' },
  { id: 18, name: '🫐' }
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

