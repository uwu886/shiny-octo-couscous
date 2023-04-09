<template>
  <nav>
    <ul>
      <li>
        <router-link to="/">首页</router-link>
      </li>
      <li>
        <router-link to="/videos">视频列表</router-link>
      </li>
      <li>
        <router-link to="/upload">上传视频</router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Navbar'
};
</script>

<style scoped>
nav {
  background-color: #333;
  padding: 10px;
}

nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
}

nav ul li {
  margin-right: 10px;
}

nav ul li a {
  color: white;
  text-decoration: none;
}
</style>
