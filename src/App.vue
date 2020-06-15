<template>
  <div id="app">
    <h1>Youtube Search</h1>
    <searchBar @inputEnter="goSearch" />
    
    <div v-if="results.length>1">
      <playVideo :playId="playId" />
      <searchList :results="results" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import searchBar from './components/searchBar.vue'
import playVideo from './components/playVideo.vue'
import searchList from './components/searchList.vue'

export default {
  name: 'App',
  components: {
    searchBar,
    playVideo,
    searchList
  },
  data(){
    return {
      results:[],
      playId:''
    }
  },
  methods:{
    goSearch(searchValue){
      const baseURL="https://www.googleapis.com/youtube/v3/search"
        const API_KEY= process.env.VUE_APP_YOUTUBE_API_KEY
        axios.get(baseURL, {
            params:{
                key:API_KEY,
                part: "snippet",
                type:'video',
                q: searchValue,
                maxResults:10,
            }
        })
        .then(response =>{
            this.results=response.data.items
            this.playId=this.results[0].id.videoId
            console.log(response.data.items)
        })
        .catch(err => {
            console.log(err)
        })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
