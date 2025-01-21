<template>
  <div class="card">
      <img :src="image" :alt="title" style="width: 100%" />
      <div className="container">
          <h1>{{ title }}</h1>
          <p class="price">{{ price }}</p>

          <router-link :to="`/products/${id}`">
              <button>Views Detail</button>
          </router-link>

      </div>
  </div>
</template>
<script>
export default {
  name: "MyCard",
  props: {
      id: {
          type: [String, Number],
          required: true,
      },
      title: {
          type: String,
          required: true,
      },
      description: {
          type: String,
          default: "",
      },
      image: {
          type: String,
          required: true
      },
      price: {
          type: [String, Number],
          required: true,
      },
  },
};
</script>
  
<style scoped>
/* Card Container */
.card {
  box-shadow: 0 4px 8px rgba(0, 149, 255, 0.2); /* เงาอ่อนสีน้ำเงิน */
  max-width: 350px;
  margin: auto;
  display: flex;
  flex-direction: column;
  background-color: #ffffff; /* สีพื้นหลังขาว */
  border-radius: 12px; /* มุมโค้งมนขึ้น */
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease; /* แอนิเมชัน */
}

.card:hover {
  transform: translateY(-8px); /* การ์ดยกขึ้น */
  box-shadow: 0 8px 16px rgba(0, 149, 255, 0.3); /* เงาเข้มขึ้นเมื่อ hover */
}

/* Image Section */
.card img {
  width: 100%; /* รูปภาพกว้างเต็มการ์ด */
  height: 200px; /* ความสูงคงที่ */
  object-fit: cover; /* ครอบรูปให้เต็ม */
  border-bottom: 2px solid #f1f1f1; /* เส้นแบ่งระหว่างรูปกับเนื้อหา */
}

/* Card Content */
.container {
  display: flex;
  flex-direction: column;
  padding: 16px;
}

.container h1 {
  font-size: 20px;
  color: #333;
  margin: 0 0 10px; /* เพิ่มระยะห่างจากด้านล่าง */
  font-weight: 600;
  text-align: center; /* ข้อความกลาง */
}

.price {
  color: #0091ff; /* สีน้ำเงินสดใส */
  font-size: 22px;
  font-weight: bold;
  text-align: center;
  margin: 10px 0; /* ระยะห่างรอบๆ ราคา */
}

/* Button */
.card button {
  border: none;
  outline: 0;
  padding: 12px;
  color: white;
  background-color: #007bff; /* สีฟ้าน้ำเงิน */
  text-align: center;
  cursor: pointer;
  font-size: 16px;
  border-radius: 6px;
  transition: background-color 0.3s ease, transform 0.2s ease; /* แอนิเมชัน */
}

.card button:hover {
  background-color: #0056b3; /* สีน้ำเงินเข้มเมื่อ hover */
  transform: scale(1.05); /* ขยายปุ่มเล็กน้อย */
  opacity: 0.9;
}
</style>
