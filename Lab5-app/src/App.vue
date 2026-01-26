<template>
  <div class="container py-5">
    <h1 class="text-center mb-5">Ứng dụng Blog nhỏ với Vue.js</h1>
    
    <div class="row">
      <div class="col-md-5">
        <CreatePost @add-post="addPost" />
      </div>

      <div class="col-md-7">
        <PostList :posts="posts" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
// Import 2 component con vào
import CreatePost from './components/CreatePost.vue';
import PostList from './components/PostList.vue';

// Dữ liệu mảng bài viết (Mặc định có sẵn 1 bài mẫu)
const posts = ref([
  {
    title: "Chào mừng đến với VueJS",
    author: "Admin",
    content: "Đây là bài viết mẫu đầu tiên.",
    backgroundColor: "#e8f4f8",
    textColor: "#000"
  }
]);

// Hàm nhận bài viết mới từ CreatePost và thêm vào mảng
function addPost(newPost) {
  posts.value.push(newPost);
}
</script>

<style>
body {
  background-color: #f8f9fa;
}
</style>