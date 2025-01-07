<script setup>
const { params } = useRoute()
const slug = params.slug

const url = slug && slug.length > 0 ? slug.join('/') : 'home'

const story = await useAsyncStoryblok(url.replace(/\/$/, ''), {
  version: 'draft',
})

if (!story?.value) {
  console.error("Data is not available")
}

</script>

<template>
  <StoryblokComponent v-if="story" :blok="story.content" />
</template>