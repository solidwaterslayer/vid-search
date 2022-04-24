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
  <h1 class="ps-5 py-1 position-absolute text-info" style="text-shadow: 2px 2px lightblue;">Vid Search</h1>

  <div class="d-flex justify-content-center py-2">
    <input aria-label="Search term" class="form-control w-50" placeholder="Search" v-model="key" v-on:keyup.enter="search"/>
    <button class="btn btn-outline-info" type="button" @click="search">Search</button>
  </div>

  <div v-if="videos && videos['data'] && videos['data']['items']">
    <div v-for="video in videos['data']['items']">
      <Video :video="video" />
    </div>
  </div>
  <div v-else>No results or there are only a limited number of searches per day.</div>
</template>
