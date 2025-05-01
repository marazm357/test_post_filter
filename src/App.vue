<script setup lang="ts">
import PostList from '@/components/PostList.vue'
import { computed, onMounted, ref } from 'vue'
import PostFilter from './components/PostFilter.vue'

const posts = ref([])
const filterText = ref('')

const fetchPostsAndCreators = async () => {
  try {
    const postRes = await fetch('https://jsonplaceholder.typicode.com/posts')
    if (!postRes.ok) throw new Error(`Ошибка при загрузке постов: ${postRes.status}`)
    const postData = await postRes.json()

    const creatorRes = await fetch('https://jsonplaceholder.typicode.com/users')
    if (!creatorRes.ok) throw new Error(`Ошибка при загрузке авторов: ${creatorRes.status}`)
    const creatorData = await creatorRes.json()

    // Проверяем, есть ли данные
    if (!postData.length || !creatorData.length) {
      throw new Error('Получены пустые данные')
    }

    const updatedPosts = postData.map((post: { title: string }) => {
      const randomCreator = creatorData[Math.floor(Math.random() * creatorData.length)]
      return {
        ...post,
        creator: randomCreator.name,
      }
    })

    posts.value = updatedPosts
  } catch (error) {
    console.error('Ошибка при загрузке данных:', error)
    posts.value = []
  }
}

const filteredPosts = computed(() =>
  posts.value.filter((post: { creator: string }) =>
    post.creator.toLowerCase().includes(filterText.value.toLowerCase()),
  ),
)

onMounted(() => {
  fetchPostsAndCreators()
})
</script>

<template>
  <div class="mainContainer">
    <PostFilter v-model:filterText="filterText" />
    <PostList :posts="filteredPosts" />
  </div>
</template>

<style scoped></style>
