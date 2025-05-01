<template>
  <div class="filterContainer">
    <div class="filterInput">
      <img class="img" src="/src/assets/lupa.png" alt="lupa" width="18px" height="18px" />
      <input
        class="input"
        type="text"
        placeholder="filter by author..."
        :value="props.filterText"
        @input="updateFilterText"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps(['filterText'])

const emit = defineEmits(['update:filterText'])

const updateFilterText = (event) => {
  emit('update:filterText', event.target.value)
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
