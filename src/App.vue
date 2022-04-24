<script lang="ts">
import ax from 'axios'
import { defineComponent } from 'vue'
import Video from './Video.vue'

export default defineComponent({
  components: {
    Video
  },
  data() {
    return {
      key: '',
      videos: null
    }
  },
  methods: {
    search() {
      ax.get('https://youtube.googleapis.com/youtube/v3/search?part=snippet&maxResults=50&q=' + this.key + '&safeSearch=none&type=video&key=AIzaSyC3BjES57YZy-QvOavWsvkSKCSytDaykzA').then((response: any) => (this.videos = response))
    }
  }
})
</script>

<template>
  <div>
    <input v-model="key" placeholder="edit me" />
    <button v-on:click="search">search</button>
  </div>

  <div v-if="videos && videos['data'] && videos['data']['items']">
    <div v-for="video in videos['data']['items']">
      <Video :video="video" />
    </div>
  </div>

  <div v-else>No results</div>
</template>
