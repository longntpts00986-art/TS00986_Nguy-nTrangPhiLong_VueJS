<template>
  <div>
    <h3 class="text-success mb-3">Danh sách bài viết</h3>
    
    <div 
      v-for="(post, index) in posts" 
      :key="index"
      :class="{ 'highlighted': post.title.length > 20 }"
      :style="{ backgroundColor: post.backgroundColor, color: post.textColor }"
      class="post-item mb-3 p-3 rounded"
    >
      <h4 class="fw-bold">{{ post.title }}</h4>
      <p class="text-secondary small">Tác giả: <span class="fw-bold">{{ post.author }}</span></p>
      <p>{{ post.content }}</p>
    </div>
  </div>
</template>

<script setup>
// Nhận dữ liệu từ App.vue truyền xuống
defineProps({
  posts: {
    type: Array,
    required: true
  }
});
</script>

<style scoped>
.post-item {
  border: 1px solid #ddd;
  transition: all 0.3s;
}

/* Class này sẽ kích hoạt khi tiêu đề dài > 20 ký tự */
.highlighted {
  border: 2px solid #ffc107; /* Viền vàng */
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}
</style>