<template>
  <div>
    <div v-for="video in videos" :key="video.id.videoId" @click="onChange(video)">
      <VideoItem :video="video" />
    </div>
  </div>
</template>

<script>
import VideoItem from "./VideoItem";

export default {
  name: "VideoList",
  components: {
    VideoItem
  },
  props: {
    videos: Array
  },
  data() {
    return { video: {} };
  },
  methods: {
    onChange(video) {
      console.log(video);
      this.$emit("onChange", video);
    }
  }
};
</script>

<style>
</style>