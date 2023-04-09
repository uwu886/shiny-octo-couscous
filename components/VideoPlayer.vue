<!-- src/components/VideoPlayer.vue -->
<template>
  <div class="video-player">
    <video controls :src="videoUrl" @ended="onVideoEnded"></video>
  </div>
</template>

<script>
export default {
  name: 'VideoPlayer',
  props: {
    videoUrl: String
  },
  methods: {
    onVideoEnded() {
      this.$emit('videoEnded');
    }
  }
};
</script>

<style scoped>
.video-player {
  width: 100%;
  text-align: center;
}

.video-player video {
  max-width: 100%;
  height: auto;
}
</style>
