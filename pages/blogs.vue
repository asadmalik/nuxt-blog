<script setup lang="ts">
  const { data: posts } = await useAsyncData('blog', () => queryCollection('blog').all())
  console.log('blogs: ', posts.value);
</script>

<template>
  <div>
    <h1>Blogs</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <NuxtLink :to="post.path">{{ post.title }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>
