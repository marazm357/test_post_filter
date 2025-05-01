<template>
  <div class="postListContainer">
    <PostItem class="postItem" v-for="post in props.posts" :key="post.id" :post="post" />
  </div>
</template>

<script setup lang="ts">
import PostItem from './PostItem.vue'

const props = defineProps(['posts'])
</script>

<style scoped>
.postListContainer {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}
.postItem {
  margin: 10px;
}
</style>
