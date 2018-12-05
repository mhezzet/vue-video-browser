<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-for="video in videos"
      :video="video"
      :key="video.snippet.title"
      @videoSelect="videoSelect"
    />
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem'

function videoSelect(video) {
  this.$emit('videoSelect', video)
}

export default {
  name: 'App',
  props: ['videos'],
  components: {
    VideoListItem
  },
  methods: {
    videoSelect
  }
}
</script>

<style>
</style>
