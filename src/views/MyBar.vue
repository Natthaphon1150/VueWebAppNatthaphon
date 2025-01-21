<template>
  <nav>
    <div class="wrapper">
      <!-- Logo Section -->
      <div class="logo">
        <router-link to="/">
          <img src="@/assets/logo.png" alt="App Logo" />
        </router-link>
      </div>

      <!-- Navigation Links -->
      <ul class="nav-links">
        <li>
          <router-link to="/">Home</router-link>
        </li>
        <li>
          <router-link to="/Products">Mycard</router-link>
        </li>
        <li>
          <router-link to="/about">About</router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
import logo from "@/assets/logo.png";

export default {
  name: "Mybar",
  data() {
    return {
      logo,
    };
  },
};
</script>

<style scoped>
/* Import Poppins Font */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600&display=swap");

/* General Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

/* Navbar */
nav {
  background-color: #ffffff; /* พื้นหลังสีขาว */
  border: 1px solid #ddd; /* กรอบบางสีเทา */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1); /* เงาเบา ๆ */
  border-radius: 8px; /* ทำขอบมน */
  position: sticky;
  top: 0;
  z-index: 1000;
  width: 100%; /* ให้ navbar เต็มความกว้างจอ */
}

.wrapper {
  width: 100%; /* ปรับให้เต็มหน้าจอ */
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
}

/* Logo */
.logo img {
  width: 100px; /* ขนาดโลโก้ */
  height: auto;
  display: block;
}

/* Navigation Links */
.nav-links {
  display: flex;
  gap: 20px;
  list-style: none;
}

.nav-links li {
  list-style: none;
}

.nav-links li a {
  text-decoration: none;
  color: #333; /* สีข้อความ */
  font-size: 18px;
  font-weight: 600;
  padding: 8px 12px;
  border-radius: 5px;
  transition: all 0.3s ease;
}

.nav-links li a:hover {
  background-color: #f0f0f0; /* สีเทาอ่อนเมื่อ hover */
  color: #0091ff; /* สีฟ้าเมื่อ hover */
}

/* Main Content */
main {
  padding: 20px;
  background-color: #ffffff; /* พื้นหลังสีขาว */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  margin: 20px auto;
  width: 100%; /* เต็มความกว้างจอ */
  min-height: calc(100vh - 100px); /* ให้เนื้อหาเต็มหน้าจอ ลบความสูง navbar */
  box-sizing: border-box; /* รวม padding ในความกว้าง */
}

/* เพิ่มเพื่อให้เนื้อหากลางหน้าจอ */
main .content {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: center;
  height: 100%; /* ให้เนื้อหาอยู่กลางหน้าจอ */
}
</style>
