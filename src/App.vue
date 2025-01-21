<script setup>
import MyBar from '@/views/MyBar.vue';

</script>

<template>
  <div id ="app">
    <MyBar />
    <router-view />
  </div>
</template>
<script>
export default {
  name : "App",
  components : {
   MyBar,
  },
};
</script>
<style scoped>
section {
  padding: 16px 24px;
  background: #f3f3f3;
  width: 100%;
  margin-right: 24px;
}

@media (min-width: 640px) {
  section {
    width: calc((100% - (24px)) / 2);
  }
}

@media (min-width: 768px) {
  section {
    width: calc((100% - (2 * 24px)) / 3);
  }
}

@media (min-width: 1024px) {
  section {
    width: calc((100% - (3 * 24px)) / 4);
  }
}

@media (min-width: 1280px) {
  section {
    width: calc((100% - (4 * 24px)) / 5);
  }
}
</style>