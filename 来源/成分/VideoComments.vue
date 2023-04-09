<!-- src/components/VideoComments.vue -->
<template>
  <div class="video-comments">
    <h3>评论</h3>
    <ul>
      <li v-for="comment in comments" :key="comment.id">
        <div class="comment-author">{{ comment.author.username }}</div>
        <div class="comment-text">{{ comment.text }}</div>
      </li>
    </ul>
    <div class="new-comment">
      <textarea v-model="newCommentText" placeholder="添加评论..."></textarea>
      <button @click="submitComment">提交</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'VideoComments',
  props: {
    videoId: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      comments: [],
      newCommentText: ''
    };
  },
  async created() {
    const response = await axios.get(`/api/videos/${this.videoId}/comments`);
    this.comments = response.data;
  },
  methods: {
    async submitComment() {
      if (!this.newCommentText.trim()) return;
      const response = await axios.post(`/api/videos/${this.videoId}/comments`, {
        text: this.newCommentText
      });
      this.comments.push(response.data);
      this.newCommentText = '';
    }
  }
};
</script>

<style scoped>
.video-comments {
  margin-top: 20px;
}

.video-comments ul {
  list-style-type: none;
  padding: 0;
}

.new-comment {
  display: flex;
  align-items: center;
  margin-top: 10px;
}

.new-comment textarea {
  flex-grow: 1;
  margin-right: 10px;
}
</style>
