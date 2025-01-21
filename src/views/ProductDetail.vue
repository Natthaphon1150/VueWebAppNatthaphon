<script setup>
import { ref, onMounted } from "vue";
import { useRoute } from "vue-router";

// กำหนด Route และ ID สินค้า
const route = useRoute();
const id = route.params.id;

// สถานะและข้อมูลสินค้า
const product = ref(null);
const loading = ref(true);
const error = ref(null);

// ดึงข้อมูลสินค้า
onMounted(() => {
  fetch(`https://fakestoreapi.com/products/${id}`)
    .then((res) => {
      if (!res.ok) throw new Error("Failed to fetch product");
      return res.json();
    })
    .then((data) => {
      product.value = data;
      loading.value = false;
    })
    .catch((err) => {
      console.error("Error fetching product:", err);
      error.value = err.message;
      loading.value = false;
    });
});
</script>

<template>
  <div class="container">
    <!-- Loading -->
    <div v-if="loading" class="status">
      <p>Loading product details...</p>
    </div>

    <!-- Error -->
    <div v-else-if="error" class="status">
      <p>Error: {{ error }}</p>
      <router-link to="/products">
        <button>Go back to the product list</button>
      </router-link>
    </div>

    <!-- Product Found -->
    <div v-else-if="product" class="content">
      <div class="left-colum">
        <img :src="product.image" :alt="product.title" />
      </div>
      <div class="right-colum">
        <div class="product-description">
          <h1>{{ product.title }}</h1>
          <p>{{ product.description }}</p>
          <p class="product-price">Price: ${{ product.price }}</p>
          <router-link to="/products">
            <button class="cart-btn">Back to Products</button>
          </router-link>
        </div>
      </div>
    </div>

    <!-- Product Not Found -->
    <div v-else>
      <h1>Product not found</h1>
      <router-link to="/products">
        <button>Go back to the product list</button>
      </router-link>
    </div>
  </div>
</template>

<style scoped>
/* ใช้ฟอนต์จาก Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&family=Roboto:wght@400;500&display=swap');

/* กำหนดฟอนต์และสีพื้นฐาน */
body {
  font-family: 'Poppins', sans-serif;
  color: #333;
  margin: 0;
  padding: 0;
  background-color: #f4f7fc;
}

/* Container */
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 2rem;
  padding: 2rem;
}

/* Status Messages */
.status p {
  font-size: 1.3rem;
  color: #555;
  text-align: center;
  font-weight: 500;
}

/* Content */
.content {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: 2rem;
  background-color: #fff;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  max-width: 1100px;
  width: 100%;
}

/* Left Column */
.left-colum img {
  width: 100%;
  max-width: 420px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Right Column */
.right-colum {
  max-width: 600px;
}

/* Product Description */
.product-description {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.product-description h1 {
  font-size: 2.2rem;
  font-weight: 600;
  color: #333;
  text-align: left;
}

.product-description p {
  font-size: 1.1rem;
  line-height: 1.6;
  color: #666;
}

.product-price {
  font-size: 1.4rem;
  color: #d9534f;
  font-weight: 600;
}

.cart-btn {
  background-color: #007bff;
  color: #fff;
  padding: 0.8rem 1.5rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease, transform 0.2s ease;
  width: fit-content;
}

.cart-btn:hover {
  background-color: #0056b3;
  transform: scale(1.05);
}

.cart-btn:focus {
  outline: none;
}

h1 {
  font-size: 2.5rem;
  color: #d9534f;
  font-weight: 600;
  text-align: center;
}

/* Button (Go back) */
button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0056b3;
}
</style>
