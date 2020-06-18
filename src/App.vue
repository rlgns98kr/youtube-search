<template>
  <div id="app">
    <div class="container">
      <div class="row align-items-center">
        <div class="col-12">
          <h1 class="text-center">Youtube Search</h1>
          <SearchBar />
        </div>
      </div>
      <div class="row">
        <div class="col-8">
          <VideoPlayer />
        </div>
        <div class="col-4">
          <VideoList />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import VideoPlayer from "./components/VideoPlayer.vue";
import VideoList from "./components/VideoList.vue";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoPlayer,
    VideoList
  }
};
</script>

<style>
</style>
