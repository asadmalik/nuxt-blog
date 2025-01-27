<script setup lang="ts">
  const route = useRoute()

  const { data: blog } = await useAsyncData('blog-' + route.path, () => {
    return queryCollection('blog').path(route.path).first()
  })

  console.log(blog, route.path);

  /*   if (!blog.value) {
      throw createError({ statusCode: 404, statusMessage: 'Oh no!!! Page not found', fatal: true })
    } */


</script>

<template>
  <ContentRenderer v-if="blog" :value="blog" />
  <div v-else>
    Blog not found at path: {{ route.fullPath }}
  </div>
</template>
