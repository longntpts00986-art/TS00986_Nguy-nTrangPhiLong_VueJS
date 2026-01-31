<template>
  <div class="container py-5">
    <h1 class="text-center mb-5 text-uppercase fw-bold text-primary">Bài Lab 6 - VueJS</h1>

    <section class="mb-5 p-4 border rounded shadow-sm bg-light">
      <h3 class="text-success">Bài 1: Xếp loại học lực</h3>
      <div class="mb-3">
        <label>Nhập điểm trung bình:</label>
        <input type="number" v-model="score" class="form-control w-50" min="0" max="10" placeholder="Nhập điểm (0-10)...">
      </div>

      <div v-if="score !== ''">
        <div v-if="score < 5" class="alert alert-danger">Xếp loại: <strong>Yếu</strong></div>
        <div v-else-if="score < 6.5" class="alert alert-warning">Xếp loại: <strong>Trung bình</strong></div>
        <div v-else-if="score < 8" class="alert alert-info">Xếp loại: <strong>Khá</strong></div>
        <div v-else-if="score < 9" class="alert alert-primary">Xếp loại: <strong>Giỏi</strong></div>
        <div v-else-if="score >= 9 && score <= 10" class="alert alert-success">Xếp loại: <strong>Xuất sắc</strong></div>
        <div v-else class="alert alert-secondary">Điểm không hợp lệ!</div>
      </div>
    </section>

    <section class="mb-5 p-4 border rounded shadow-sm bg-light">
      <h3 class="text-success">Bài 2: Mùa trong năm</h3>
      <div class="mb-3">
        <label>Nhập tháng (1-12):</label>
        <input type="number" v-model="month" class="form-control w-50" placeholder="Nhập tháng...">
      </div>

      <div v-if="month">
        <p v-if="month >= 1 && month <= 3" class="fw-bold text-success">🌸 Mùa Xuân</p>
        <p v-else-if="month >= 4 && month <= 6" class="fw-bold text-danger">☀️ Mùa Hè</p>
        <p v-else-if="month >= 7 && month <= 9" class="fw-bold text-warning">🍂 Mùa Thu</p>
        <p v-else-if="month >= 10 && month <= 12" class="fw-bold text-info">❄️ Mùa Đông</p>
        <p v-else class="text-danger fw-bold">Vui lòng nhập tháng từ 1 đến 12!</p>
      </div>
    </section>

    <section class="p-4 border rounded shadow-sm bg-white">
      <h3 class="text-danger mb-4">Bài 3 & 4: Quản lý học sinh (CRUD)</h3>
      
      <div class="card p-3 mb-4 bg-light">
        <h5 class="mb-3">{{ isEditing ? 'Cập nhật thông tin' : 'Thêm học sinh mới' }}</h5>
        <form @submit.prevent="submitForm" class="row g-3">
          <div class="col-md-4">
            <label class="form-label">Họ tên:</label>
            <input v-model="student.name" type="text" class="form-control" required>
          </div>
          <div class="col-md-3">
            <label class="form-label">Điểm số:</label>
            <input v-model="student.score" type="number" min="0" max="10" class="form-control" required>
          </div>
          <div class="col-md-3">
            <label class="form-label">Ngày sinh:</label>
            <input v-model="student.dob" type="date" class="form-control" required>
          </div>
          <div class="col-md-2 d-flex align-items-end">
 <button 
  type="submit"
  class="btn w-100 fw-bold shadow-sm d-flex align-items-center justify-content-center py-2" 
  :class="isEditing ? 'btn-warning' : 'btn-success'"
  style="min-height: 48px; font-size: 1.1rem;"
>
  <span class="me-2">{{ isEditing ? '💾' : '➕' }}</span>
  <span>{{ isEditing ? 'LƯU' : 'THÊM' }}</span>
</button>
</div>
        </form>
      </div>

      <table class="table table-hover table-bordered">
        <thead class="table-primary">
          <tr>
            <th>Họ và tên</th>
            <th>Điểm</th>
            <th>Ngày sinh</th>
            <th>Hành động</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(st, index) in students" :key="index">
            <td>{{ st.name }}</td>
            <td>{{ st.score }}</td>
            <td>{{ st.dob }}</td>
            <td>
              <button class="btn btn-sm btn-info me-2" @click="editStudent(index)">Sửa</button>
              <button class="btn btn-sm btn-danger" @click="deleteStudent(index)">Xóa</button>
            </td>
          </tr>
        </tbody>
      </table>
    </section>

  </div>
</template>

<script setup>
import { ref } from 'vue';

// --- LOGIC BÀI 1 ---
const score = ref('');

// --- LOGIC BÀI 2 ---
const month = ref('');

// --- LOGIC BÀI 3 & 4 (QUẢN LÝ SINH VIÊN) ---
// Danh sách sinh viên mẫu
const students = ref([
  { name: 'Nguyễn Văn A', score: 8.5, dob: '2004-01-15' },
  { name: 'Trần Thị B', score: 6.0, dob: '2005-05-20' }
]);

// Biến quản lý form
const student = ref({
  name: '',
  score: null,
  dob: ''
});

// Biến trạng thái (đang thêm hay đang sửa)
const isEditing = ref(false);
const editingIndex = ref(null);

// Hàm xử lý khi bấm nút Submit (Thêm hoặc Sửa)
function submitForm() {
  if (isEditing.value) {
    // Logic cập nhật (Sửa)
    students.value[editingIndex.value] = { ...student.value };
    isEditing.value = false;
    editingIndex.value = null;
  } else {
    // Logic thêm mới
    students.value.push({ ...student.value });
  }
  resetForm();
}

// Hàm chuẩn bị dữ liệu để sửa
function editStudent(index) {
  // Copy dữ liệu dòng được chọn lên form
  student.value = { ...students.value[index] };
  isEditing.value = true;
  editingIndex.value = index;
}

// Hàm xóa sinh viên
function deleteStudent(index) {
  if (confirm('Bạn có chắc chắn muốn xóa không?')) {
    students.value.splice(index, 1);
  }
}

// Hàm làm mới form
function resetForm() {
  student.value = { name: '', score: null, dob: '' };
}
</script>

<style scoped>
/* Không cần CSS nhiều vì đã dùng Bootstrap */
</style>