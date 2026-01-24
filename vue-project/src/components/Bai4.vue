<template>
  <div class="container mt-6">
    <h1 class="text-center">Kiến thức sức khỏe cộng đồng</h1>
    <div class="row">
      <div class="col-sm-6">
        <div class="card">
          <img :src="items[0].image" alt="Hình ảnh" class="card-img-top" />
          <div class="card-body">
            <h3 class="card-title">{{ items[0].title }}</h3>
            <p class="card-text">{{ items[0].content }}</p>
            <button class="btn btn-info">Xem chi tiết</button>
          </div>
        </div>
      </div>
      <div class="col-sm-4">
        <div class="card">
          <img :src="items[1].image" alt="Hình ảnh" class="card-img-top" />
          <div class="card-body">
            <h3 class="card-title">{{ items[1].title }}</h3>
            <p class="card-text">{{ items[1].content }}</p>
            <button class="btn btn-info">Xem chi tiết</button>
          </div>
        </div>
      </div>
      <div class="col-sm-4">
        <div class="card">
          <img :src="items[2].image" alt="Hình ảnh" class="card-img-top" />
          <div class="card-body">
            <h3 class="card-title">{{ items[2].title }}</h3>
            <p class="card-text">{{ items[2].content }}</p>
            <button class="btn btn-info">Xem chi tiết</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// Dùng ../ để thoát ra khỏi thư mục components tìm về assets
// Chú ý đuôi .png và tên file chính xác
import img1 from '../assets/images/corevalue.jpg';
import img2 from '../assets/images/eat-clean.png'; 
import img3 from '../assets/images/orange_300x300 copy.jpg'; // Tên file có dấu cách dễ lỗi, tốt nhất nên đổi tên file ngắn gọn lại (ví dụ orange.jpg)

const items = [
  { 
    title: '8 loại rau củ quả giàu canxi', 
    content: 'Canxi là...', 
    image: img1 
  },
  { 
    title: 'Các loại gia vị tốt cho sức khỏe', 
    content: 'Một số loại...', 
    image: img2
  },
  { 
    title: '9 loại đậu bổ dưỡng nên dùng nhiều', 
    content: 'Đậu lăng...', 
    image: img3
  },
];
</script>