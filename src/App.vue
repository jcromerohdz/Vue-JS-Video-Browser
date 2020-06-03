<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
  </div>
</template>

<script>
//import axios from 'axios'
import youtube from './apis/youtubeapi';
import SearchBar from './components/SearchBar'
const API_KEY = 'AIzaSyA9tHarzPMsBCdwtsgrgwFVxhCYZC2HKIc'

export default {
 name: 'App',
 components: {
   SearchBar
 },
 methods: {
   onTermChange(searchTerm){
     youtube.get("/search",{
       params: {
         key: API_KEY,
         type: 'video',
         part: 'snippet',
         q: searchTerm
       }
     })
     .then(response => console.log(response))
     .catch(err => console.log(err))
         
   }
 }
}
</script>