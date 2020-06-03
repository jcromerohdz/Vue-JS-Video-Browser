<template>
  <ul>
    VideoList
    <VideoListItem 
    v-for="video in videos" 
    :key="video.snippet.id"
    :video="video"
    > 
  
    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
  name: 'VideoList',
  components:{
    VideoListItem
  },
  props: {
    videos: Array
  }
}
</script>

<style scoped>

</style>