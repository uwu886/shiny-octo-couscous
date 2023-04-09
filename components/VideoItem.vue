<!-- src/components/VideoItem.vue -->
<template>
  <div class="video-item">
    <img :src="video.thumbnail" :alt="video.title" />
    <h3>{{ video.title }}</h3>
  </div>
</template>

<script>
export default {
  name: 'VideoItem',
  props: {
    video: Object
  }
};
</script>

<style scoped>
.video-item {
  display: flex;
  align-items: center;
}

.video-item img {
  width: 100px;
  height: 60px;
  margin-right: 10px;
}

.video-item h3 {
  margin: 0;
}
</style>
