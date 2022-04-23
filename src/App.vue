<script lang="ts">
import ax from 'axios'
import { defineComponent } from 'vue'

export default defineComponent({
  data() {
    return {
      count: null
    }
  },
  mounted() {
    ax.get('https://youtube.googleapis.com/youtube/v3/search?part=snippet&q=bob&key=AIzaSyCkkMO5kQ4kI2F_hRbS_QeXVYxdVjz0-9Q').then((response: any) => (this.count = response))
  }
})
</script>

<template>
  {{ count }}
  <table class="table">
    <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">First</th>
        <th scope="col">Last</th>
        <th scope="col">Handle</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th scope="row">1</th>
        <td>Mark</td>
        <td>Otto</td>
        <td>@mdo</td>
      </tr>
      <tr>
        <th scope="row">2</th>
        <td>Jacob</td>
        <td>Thornton</td>
        <td>@fat</td>
      </tr>
      <tr>
        <th scope="row">3</th>
        <td colspan="2">Larry the Bird</td>
        <td>@twitter</td>
      </tr>
    </tbody>
  </table>
  <div class="card" style="width: 18rem;">
    <ul class="list-group list-group-flush">
      <li class="list-group-item">An item</li>
      <li class="list-group-item">A second item</li>
      <li class="list-group-item">A third item</li>
    </ul>
  </div>
</template>

<style>
</style>
