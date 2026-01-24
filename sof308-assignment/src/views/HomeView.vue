<script setup>
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

// Dữ liệu giả mô phỏng danh sách bài viết (Sau này sẽ lấy từ API)
const posts = ref([
  {
    id: 1,
    title: 'Giới thiệu về Vue.js',
    excerpt: 'Vue.js là một framework JavaScript tiến bộ dùng để xây dựng giao diện người dùng...',
    author: 'Admin',
    image: 'https://placehold.co/600x400?text=VueJS'
  },
  {
    id: 2,
    title: 'Học Bootstrap 5 cơ bản',
    excerpt: 'Bootstrap giúp thiết kế website nhanh chóng và chuẩn responsive trên mọi thiết bị...',
    author: 'Nguyen Van A',
    image: 'https://placehold.co/600x400?text=Bootstrap'
  },
  {
    id: 3,
    title: 'Kỹ năng Debug code hiệu quả',
    excerpt: 'Tìm hiểu các công cụ và phương pháp để sửa lỗi code nhanh chóng trong VS Code...',
    author: 'Tran Thi B',
    image: 'https://placehold.co/600x400?text=Coding'
  }
])
</script>

<template>
  <div class="home-page">
    <div class="p-5 mb-4 bg-light rounded-3 border">
      <div class="container-fluid py-3">
        <h1 class="display-5 fw-bold">Chào mừng đến với Blog SOF308</h1>
        <p class="col-md-8 fs-4">Nơi chia sẻ kiến thức về lập trình, công nghệ và cuộc sống sinh viên FPT Polytechnic.</p>
        <button class="btn btn-primary btn-lg" type="button">Khám phá ngay</button>
      </div>
    </div>

    <div class="row">
      <div class="col-12 mb-3">
        <h3 class="border-bottom pb-2">Bài viết mới nhất</h3>
      </div>

      <div class="col-md-6 col-lg-4 mb-4" v-for="post in posts" :key="post.id">
        <div class="card h-100 shadow-sm">
          <img :src="post.image" class="card-img-top" :alt="post.title">
          <div class="card-body">
            <h5 class="card-title">{{ post.title }}</h5>
            <p class="card-text text-muted small">Tác giả: {{ post.author }}</p>
            <p class="card-text">{{ post.excerpt }}</p>
            
            <RouterLink :to="'/post/' + post.id" class="btn btn-outline-primary btn-sm">
              Đọc tiếp
            </RouterLink>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* CSS riêng cho trang Home nếu cần */
.card-img-top {
  height: 200px;
  object-fit: cover;
}
</style>