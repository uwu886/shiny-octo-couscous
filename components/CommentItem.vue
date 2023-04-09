<!-- src/components/CommentItem.vue -->
<template>
  <div class="comment-item">
    <div class="comment-author">{{ comment.author }}</div>
    <div class="comment-content">{{ comment.content }}</div>
  </div>
</template>

<script>
export default {
  name: 'CommentItem',
  props: {
    comment: Object
  }
};
</script>

<style scoped>
.comment-item {
  display: flex;
  flex-direction: column;
  border-bottom: 1px solid #ccc;
  padding: 10px;
}

.comment-author {
  font-weight: bold;
}
</style>
