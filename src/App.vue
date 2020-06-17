<template>
  <div id="app">
    <div class="container">
      <div class="row align-items-center">
        <div class="col-12">
          <h1 class="text-center">Youtube Search</h1>
          <SearchBar @onInput="getVideos" />
        </div>
      </div>
      <div class="row">
        <div class="col-8">
          <VideoPlayer :video="video" />
        </div>
        <div class="col-4">
          <VideoList @onChange="changeVideo" :videos="videos" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

import SearchBar from "./components/SearchBar.vue";
import VideoPlayer from "./components/VideoPlayer.vue";
import VideoList from "./components/VideoList.vue";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoPlayer,
    VideoList
  },
  data() {
    return {
      videos: [],
      video: {}
    };
  },
  methods: {
    changeVideo(userClick) {
      this.video = userClick;
    },
    getVideos(userInput) {
      // 1. 입력된 검색어를 가지고,
      const baseURL = "https://www.googleapis.com/youtube/v3/search";
      const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY;
      // 2. Youtube API에 요청을 보내어
      axios
        .get(baseURL, {
          params: {
            // key, part, q
            key: API_KEY,
            part: "snippet",
            type: "video",
            q: userInput,
            maxResults: 10
          }
        })
        .then(response => {
          this.videos = response.data.items;
        });
      // 3. 검색어로 검색한 결과를 가져옴
    }
  }
};
</script>

<style>
</style>
