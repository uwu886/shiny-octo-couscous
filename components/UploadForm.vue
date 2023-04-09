<!-- src/components/UploadForm.vue -->
<template>
  <form @submit.prevent="onSubmit" enctype="multipart/form-data">
    <label for="title">视频标题:</label>
    <input type="text" id="title" v-model="title" required />

    <label for="video-file">选择视频:</label>
    <input type="file" id="video-file" @change="onFileChange" required />

    <button type="submit">上传</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  name: 'UploadForm',
  data() {
    return {
      title: '',
      file: null
    };
  },
  methods: {
    onFileChange(e) {
      this.file = e.target.files[0];
    },
    async onSubmit() {
      if (!this.file) {
        alert('请选择一个视频文件');
        return;
      }

      const formData = new FormData();
      formData.append('title', this.title);
      formData.append('file', this.file);

      try {
        await axios.post('/api/videos', formData, {
          headers: {
            'Content-Type': 'multipart/form-data'
          }
        });
        alert('视频上传成功');
        this.title = '';
        this.file = null;
      } catch (error) {
        alert('视频上传失败');
      }
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
