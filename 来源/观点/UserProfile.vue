<!-- src/views/UserProfile.vue -->
<template>
  <div class="user-profile">
    <h2>{{ user.username }} 的个人主页</h2>
    <div class="user-info">
      <img :src="user.avatar" alt="头像" />
      <p>邮箱：{{ user.email }}</p>
      <p>粉丝数：{{ user.followers }}</p>
    </div>
    <div class="user-videos">
      <h3>上传的视频</h3>
      <video-item v-for="video in userVideos" :key="video.id" :video="video" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import VideoItem from '@/components/VideoItem.vue';

export default {
  name: 'UserProfile',
  components: {
    VideoItem
  },
  data() {
    return {
      user: {},
      userVideos: []
    };
  },
  async created() {
    const userId = this.$route.params.id; // 假设我们从路由中获取用户 ID
    const [userResponse, videosResponse] = await Promise.all([
      axios.get(`/api/users/${userId}`),
      axios.get(`/api/users/${userId}/videos`)
    ]);

    this.user = userResponse.data;
    this.userVideos = videosResponse.data;
  }
};
</script>

<style scoped>
.user-profile {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.user-info {
  display: flex;
  align-items: center;
}

.user-info img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border-radius: 50%;
  margin-right: 20px;
}

.user-videos {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}
</style>
