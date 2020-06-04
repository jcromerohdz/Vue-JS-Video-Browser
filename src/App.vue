<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
  </div>
</template>

<script>
import youtube from './apis/youtubeapi'
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'

const API_KEY = 'AIzaSyA9tHarzPMsBCdwtsgrgwFVxhCYZC2HKIc'

export default {
 name: 'App',
 components: {
   SearchBar,
   VideoList,
 },
 data(){
   return { videos: [] }
 },
 methods: {
   onVideoSelect(video) {
     console.log(video)
   },
   onTermChange(searchTerm){
     youtube.get("/search",{
       params: {
         key: API_KEY,
         type: 'video',
         part: 'snippet',
         q: searchTerm
       }
     })
     .then(response => {
       this.videos = response.data.items
     })
     .catch(err => console.log(err))
         
   }
 }
}
</script>