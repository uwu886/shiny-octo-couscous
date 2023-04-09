<!-- src/components/FollowerList.vue -->
<template>
  <div class="follower-list">
    <h3>粉丝</h3>
    <ul>
      <li v-for="follower in followers" :key="follower.id">
        {{ follower.username }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'FollowerList',
  props: {
    userId: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      followers: []
    };
  },
  async created() {
    const response = await axios.get(`/api/users/${this.userId}/followers`);
    this.followers = response.data;
  }
};
</script>

<style scoped>
.follower-list {
  margin-top: 20px;
}

.follower-list ul {
  list-style-type: none;
  padding: 0;
}
</style>
