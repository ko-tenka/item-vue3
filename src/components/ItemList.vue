<template>
  <div class="item-list">
    <h3>{{ title }}</h3>
    <div class="items-row">
      <div
        v-for="item in items"
        :key="item.id"
        class="item"
        :class="{ selected: isSelected(item) }"
        @click="toggleSelect(item)"
      >
        {{ item.name }}
      </div>
    </div>
  </div>
</template>

<script setup>
import { toRefs, computed } from 'vue'
const props = defineProps({
  title: String,
  items: Array,
  selectedItems: [Array, Object, null],
  single: Boolean
})
const emit = defineEmits(['update:selectedItems'])

function isSelected(item) {
  if (props.single) {
    return props.selectedItems && props.selectedItems.id === item.id
  } else {
    return Array.isArray(props.selectedItems) && props.selectedItems.some(i => i.id === item.id)
  }
}

function toggleSelect(item) {
  if (props.single) {
    if (props.selectedItems && props.selectedItems.id === item.id) {
      emit('update:selectedItems', null)
    } else {
      emit('update:selectedItems', item)
    }
  } else {
    let newSelected = Array.isArray(props.selectedItems) ? [...props.selectedItems] : []

    if (newSelected.some(i => i.id === item.id)) {
      newSelected = newSelected.filter(i => i.id !== item.id)
    } else {
      if (newSelected.length < 6) {
        newSelected.push(item)
      } else {
        alert('Можно выбрать максимум 6 предметов')
        return
      }
    }

    emit('update:selectedItems', newSelected)
  }
}

</script>


<style scoped>
.item-list {
  border: 1px solid #ccc;
  padding: 10px;
  border-radius: 8px;
  background: #fafafa;
}

.items-row {
  display: flex;
  gap: 10px;
  flex-wrap: nowrap;
  overflow-x: auto;
  padding: 10px 0;
}

.item {
  padding: 8px 16px;
  border: 1px solid #bbb;
  border-radius: 6px;
  background-color: white;
  cursor: pointer;
  user-select: none;
  white-space: nowrap;
  transition: background-color 0.3s, border-color 0.3s;
}

.item.selected {
  background-color:rgb(234, 190, 240);
  border-color:rgb(114, 76, 175);
  color: white;
}
</style>

