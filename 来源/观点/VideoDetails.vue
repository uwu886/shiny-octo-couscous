<!-- src/views/VideoDetails.vue -->
<template>
  <!-- ... -->
  <div class="video-info">
    <!-- ... -->
  </div>
  <video-comments :videoId="video.id" />
</template>

<script>
import VideoComments from '@/components/VideoComments.vue';
// ...

export default {
  // ...
  components: {
    VideoComments
  },
  // ...
};
</script>

<!-- src/views/VideoDetails.vue -->
<template>
  <!-- ... -->
  <div class="video-info">
    <!-- ... -->
    <button @click="likeVideo">{{ video.likes }} 赞</button>
  </div>
  <!-- ... -->
</template>

<script>
// ...

export default {
  // ...
  methods: {
    async likeVideo() {
      const response = await axios.post(`/api/videos/${this .video.id}/likes`);
this.video.likes = response.data.likes;
},
// ...
},
// ...
};
</script>

