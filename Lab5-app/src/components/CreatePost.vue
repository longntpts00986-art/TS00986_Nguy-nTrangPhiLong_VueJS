<template>
  <div class="card p-4 mb-4 shadow-sm border-primary">
    <h3 class="text-primary">Tạo bài viết mới</h3>
    
    <div class="mb-3">
      <label class="form-label">Tiêu đề bài viết:</label>
      <input v-model="title" type="text" class="form-control" placeholder="Nhập tiêu đề..." />
    </div>

    <div class="mb-3">
      <label class="form-label">Tác giả:</label>
      <input v-model="author" type="text" class="form-control" placeholder="Nhập tên tác giả..." />
    </div>

    <div class="mb-3">
      <label class="form-label">Nội dung:</label>
      <textarea v-model="content" class="form-control" rows="3" placeholder="Nhập nội dung..."></textarea>
    </div>

    <button class="btn btn-primary w-100" @click="submitPost">Đăng bài</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Định nghĩa sự kiện để gửi dữ liệu ra ngoài (cho App.vue nhận)
const emit = defineEmits(['add-post']);

const title = ref('');
const content = ref('');
const author = ref('');

function submitPost() {
  if (title.value && content.value && author.value) {
    // Tạo đối tượng bài viết mới
    const newPost = {
      title: title.value,
      content: content.value,
      author: author.value,
      // Random màu nền nhẹ nhàng để test Style Binding
      backgroundColor: `hsl(${Math.random() * 360}, 70%, 90%)`,
      textColor: '#333'
    };

    // Gửi sự kiện 'add-post' kèm dữ liệu newPost ra ngoài
    emit('add-post', newPost);

    // Reset ô nhập liệu sau khi đăng
    title.value = '';
    content.value = '';
    author.value = '';
  } else {
    alert('Vui lòng nhập đầy đủ thông tin!');
  }
}
</script>