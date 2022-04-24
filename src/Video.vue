<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  props: ['video']
})
</script>

<template>
  <pre>{{ video }}</pre>
</template>
