<template>
  <header class="header">
    <div class="header-container">
      <h1 class="logo">🍳 Cooking <span>Masterclass</span></h1>
      <div class="wishlist-badge">
        ❤️ Wishlist: <span>{{ wishlistCount }}</span>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  // This prop allows App.vue to pass down the total count dynamically
  props: {
    wishlistCount: {
      type: Number,
      required: true
    }
  }
}
</script>

<style scoped>
.header {
  background-color: white;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
  padding: 20px 0;
  position: sticky;
  top: 0;
  z-index: 100;
}
.header-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}
.logo span {
  color: #e65c00; /* Warm culinary orange accent */
}
.wishlist-badge {
  background-color: #2c3e50;
  color: white;
  padding: 8px 16px;
  border-radius: 20px;
  font-weight: bold;
}
.wishlist-badge span {
  color: #e65c00;
}
</style>