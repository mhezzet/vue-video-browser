<template>
  <div class="container">
    <SearchBar @termChange="termChangeHandler"/>
    <div class="row">
      <VideoDetail class="VideoDetail" :video="selectedVideo"/>
      <VideoList class="VideoList" :videos="videos" @videoSelect="videoSelectHandler"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetail from './components/VideoDetail'

const API_KEY = 'AIzaSyD5zsx7rk-eJFPywJXBJinOBMX8ijKSSgk'
const state = { videos: [], selectedVideo: null }

async function termChangeHandler(searchTerm) {
  const response = await axios.get(
    `https://www.googleapis.com/youtube/v3/search`,
    {
      params: {
        key: API_KEY,
        type: 'video',
        part: 'snippet',
        q: searchTerm
      }
    }
  )

  this.videos = response.data.items
  this.selectedVideo = this.videos[0]
}

function videoSelectHandler(video) {
  this.selectedVideo = video
}

export default {
  data: () => state,
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  methods: {
    termChangeHandler,
    videoSelectHandler
  }
}
</script>

<style scoped>
</style>
