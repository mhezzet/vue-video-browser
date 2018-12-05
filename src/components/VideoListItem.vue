<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="mr-3" :src="video.snippet.thumbnails.default.url">
    <div class="media-body">{{video.snippet.title}}</div>
  </li>
</template>

<script>
function onVideoSelect() {
  this.$emit('videoSelect', this.video)
}

export default {
  name: 'VideoListItem',
  props: ['video'],
  methods: {
    onVideoSelect
  }
}
</script>

<style scoped>
li {
  display: flex;
  align-items: center;
  cursor: pointer;
}

li:hover {
  background-color: aliceblue;
}
</style>
