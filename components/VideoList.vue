<!-- src/components/VideoList.vue -->
<template>
  <div class="video-list">
    <video-item v-for="video in videos" :key="video.id" :video="video"></video-item>
  </div>
</template>

<script>
import axios from 'axios';
import VideoItem from './VideoItem.vue';

export default {
  name: 'VideoList',
  components: {
    VideoItem
  },
  data() {
    return {
      videos: []
    };
  },
  async created() {
    const response = await axios.get('/api/videos');
    this.videos = response.data;
  }
};
</script>

<style scoped>
.video-list {
  display: flex;
  flex-wrap: wrap;
}

.video-item {
  width: 33.33%;
  padding: 15px;
}
</style>
