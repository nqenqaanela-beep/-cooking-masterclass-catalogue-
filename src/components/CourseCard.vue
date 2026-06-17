<template>
  <div class="course-card">
    <div class="card-image-wrapper">
      <img :src="course.image" :alt="course.title" class="course-image" />
    </div>

    <div class="card-content">
      <div class="card-meta">
        <span class="badge">{{ course.category }}</span>
        <span class="rating">⭐ {{ course.rating }}</span>
      </div>
      
      <h3 class="course-title">{{ course.title }}</h3>
      <p class="course-chef">Chef: {{ course.chef }}</p>
      <p class="course-description">{{ course.description }}</p>
      
      <div class="card-footer">
        <span class="course-price">R{{ course.price }}</span>
        
        <button 
          @click="$emit('toggle-wishlist', course.id)" 
          :class="['wishlist-btn', { 'is-active': isWishlisted }]"
        >
          {{ isWishlisted ? '❤️ Saved' : '🤍 Wishlist' }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // Define incoming data blocks and active selection indicators
  props: {
    course: {
      type: Object,
      required: true
    },
    isWishlisted: {
      type: Boolean,
      default: false
    }
  },
  emits: ['toggle-wishlist']
}
</script>

<style scoped>
.course-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.course-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.card-image-wrapper {
  position: relative;
  width: 100%;
  padding-top: 56.25%; /* Fixed 16:9 widescreen ratio */
  background-color: #f5f5f5;
}

.course-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.card-content {
  padding: 20px;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.card-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}

.badge {
  background-color: #ffe6d5;
  color: #e65c00;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: bold;
}

.rating {
  font-size: 0.9rem;
  font-weight: bold;
  color: #555;
}

.course-title {
  font-size: 1.2rem;
  margin: 0 0 6px 0;
  color: #2c3e50;
}

.course-chef {
  font-size: 0.85rem;
  color: #7f8c8d;
  margin-bottom: 12px;
}

.course-description {
  font-size: 0.9rem;
  color: #555;
  line-height: 1.4;
  margin-bottom: 20px;
  flex-grow: 1; /* Pushes the card footer elements to align at the bottom */
}

.card-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 15px;
  border-top: 1px solid #f0f0f0;
}

.course-price {
  font-size: 1.25rem;
  font-weight: bold;
  color: #2c3e50;
}

.wishlist-btn {
  background: none;
  border: 1px solid #ddd;
  padding: 8px 14px;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 500;
  font-size: 0.9rem;
  transition: all 0.2s ease;
}

.wishlist-btn:hover {
  background-color: #fff5f5;
  border-color: #ff9999;
}

.wishlist-btn.is-active {
  background-color: #ff4d4d;
  color: white;
  border-color: #ff4d4d;
}
</style>