<script setup>
import MyCard from '@/views/MyCard.vue';
</script>

<template>
  <main>
    <!-- Section Title -->
    <div class="tx">
      <h1>Products</h1>
    </div>

    <!-- Loading State -->
    <p v-if="isLoading" class="loading-text">Loading products...</p>
    <p v-else-if="items.length === 0" class="no-data">No products available.</p>

    <!-- Grid Container -->
    <div v-if="!isLoading && items.length > 0" class="grid-container">
      <MyCard
        v-for="item in items"
        :key="item.id"
        :id="item.id"
        :title="item.title"
        :description="item.description"
        :image="item.image"
        :price="item.price"
      />
    </div>
  </main>
</template>

<script>
export default {
  name: "Products",
  components: {
    MyCard,
  },
  data() {
    return {
      items: [],
      isLoading: true, // ใช้สำหรับโหลดข้อมูล
    };
  },
  created() {
    fetch("https://fakestoreapi.com/products")
      .then((res) => res.json())
      .then((json) => {
        this.items = json;
        this.isLoading = false; // โหลดเสร็จแล้ว
      })
      .catch((error) => {
        console.error("Error fetching products:", error);
        this.isLoading = false;
      });
  },
};
</script>

<style scoped>
/* ใช้ฟอนต์จาก Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&family=Roboto:wght@400;500&display=swap');

/* Main Container */
main {
  background: linear-gradient(to bottom, #e3f2fd, #ffffff); /* พื้นหลังไล่สี */
  padding: 2rem;
  margin: 0;
  font-family: 'Poppins', sans-serif;
}

/* Section Title */
.tx {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2.5rem;
  font-weight: 600;
  color: #007bff;
}

/* Loading Text */
.loading-text,
.no-data {
  text-align: center;
  font-size: 1.2rem;
  color: #555;
}

/* Grid Container */
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}

/* Media Queries */
@media (max-width: 768px) {
  .tx {
    font-size: 2rem;
  }

  main {
    padding: 1rem;
  }

  .grid-container {
    gap: 1rem; /* ลดช่องว่างระหว่างการ์ด */
  }
}

@media (max-width: 576px) {
  .tx {
    font-size: 1.5rem;
  }

  .grid-container {
    gap: 0.5rem; /* ลดช่องว่างเพิ่มสำหรับหน้าจอเล็ก */
  }
}
</style>
