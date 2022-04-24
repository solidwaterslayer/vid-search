<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  methods: {
    redirect() {
      window.open('https://www.youtube.com/watch?v=' + this.video.id.videoId, '_blank')
    }
  },
  props: ['video']
})
</script>

<template>
  <div class="hover mb-3" @click="redirect" tabindex="0">
    <div class="row mx-0">
      <div class="col-1"></div>
      <div class="col-4 d-flex justify-content-end">
        <img :src="video.snippet.thumbnails.medium.url" class="img-thumbnail">
      </div>
      <div class="col-6">
        <h5 class="py-1">{{ video.snippet.title }}</h5>
        <p>Date: {{ video.snippet.publishTime }}</p>
        <p>Channel: {{ video.snippet.channelTitle }}</p>
        <p>Description: {{ video.snippet.description }}</p>
      </div>
      <div class="col-1"></div>
    </div>
  </div>
</template>

<style>
.hover {
  cursor: pointer;
  transition: 250ms;
}

.hover:hover {
  box-shadow: 10px 10px 10px 10px red;
}
</style>
