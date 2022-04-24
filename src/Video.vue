<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  props: ['video']
})
// 
</script>

<template>
  <p>{{ 'https://www.youtube.com/watch?v=' + video.id.videoId }}</p>
  <p>{{ video.snippet.thumbnails.medium.url }}</p>
  <p>{{ video.snippet.title }}</p>
  <p>{{ video.snippet.publishTime }}</p>
  <p>{{ video.snippet.channelTitle }}</p>
  <p>{{ video.snippet.description }}</p>
</template>
