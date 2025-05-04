<template>
  <div class="filterContainer">
    <div class="filterInput">
      <img class="img" src="/src/assets/lupa.png" alt="lupa" width="18px" height="18px" />
      <input class="input" type="text" placeholder="filter by author..." v-model="filterText"
        @input="updateFilterText" />
    </div>
  </div>
</template>

<script setup lang="ts">
const filterText = defineModel()

// const props = defineProps(['filterText'])

const emit = defineEmits(['update:filterText'])

const updateFilterText = () => {
  emit('update:filterText', filterText.value)
}
</script>

<style scoped>
.filterContainer {
  margin: 20px 0px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.filterInput {
  display: flex;
  background-color: white;
  border-radius: 15px;
}

.input {
  border: none;
}

.img {
  padding: 5px;
}
</style>
