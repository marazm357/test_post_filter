<template>
  <div class="postItemContainer">
    <div class="postItemTitle">{{ props.post.title }}</div>
    <div class="postItemBody">{{ props.post.body }}</div>
    <div class="postItemCreator">{{ props.post.creator }}</div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps(['post'])
</script>

<style scoped>
.postItemContainer {
  background-color: white;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 10px;
}
.postItemTitle {
  color: #5195e5;
  font-size: 20px;
  margin-bottom: 10px;
}

.postItemBody {
  overflow: hidden;
}

.postItemCreator {
  margin-top: 15px;
  color: #d7d9dc;
  align-self: flex-start;
  font: 200;
}
</style>
