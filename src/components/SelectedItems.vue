<template>
  <div class="selected-items">
    <h3>{{ title }}</h3>
    <div class="items-row">
      <div v-for="item in items" :key="item.id" class="item">
        {{ item.name }}
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  title: String,
  items: Array
})
</script>

<style scoped>
.selected-items {
  border: 1px solid #ccc; /* рамка вокруг всего блока */
  padding: 10px;
  border-radius: 8px;
  background: #f0f0f0;
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
  white-space: nowrap;
  user-select: none;
}
</style>

