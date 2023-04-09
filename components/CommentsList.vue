<!-- src/components/CommentsList.vue -->
<template>
  <div class="comments-list">
    <h3>评论</h3>
    <comment-item v-for="comment in comments" :key="comment.id" :comment="comment"></comment-item>
  </div>
</template>

<script>
import axios from 'axios';
import CommentItem from './CommentItem.vue';

export default {
  name: 'CommentsList',
  components: {
    CommentItem
  },
  props: {
    videoId: Number
  },
  data() {
    return {
      comments: []
    };
  },
  async created() {
    const response = await axios.get(`/api/videos/${this.videoId}/comments`);
    this.comments = response.data;
  }
};
</script>

<style scoped>
.comments-list {
  display: flex;
  flex-direction: column;
}
</style>
