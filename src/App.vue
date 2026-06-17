<template>
  <div class="app-container">
    <AppHeader :wishlistCount="wishlist.length" />

    <main class="main-content">
      <div class="hero-section">
        <h2>Master the Art of Cooking</h2>
        <p>Explore our exclusive, chef-hosted interactive culinary workshops.</p>
      </div>

      <div class="catalog-grid">
        <CourseCard 
          v-for="item in courses" 
          :key="item.id"
          :course="item"
          :isWishlisted="wishlist.includes(item.id)"
          @toggle-wishlist="toggleWishlistHandler"
        />
      </div>
    </main>
  </div>
</template>

<script>
// Import our newly created custom building blocks
import AppHeader from './components/AppHeader.vue'
import CourseCard from './components/CourseCard.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    CourseCard
  },
  data() {
    return {
      // Array storing the unique IDs of saved workshops
      wishlist: [],
      
      // Dynamic catalog data array containing the required details
      courses: [
        {
          id: 1,
          title: 'Artisanal Italian Pizza Crafting',
          chef: 'Giovanni Rossi',
          category: 'Baking',
          price: 650,
          rating: 4.9,
          description: 'Learn the secrets of fermentation, hand-stretching dough, and balancing classic wood-fired toppings.',
          image: 'https://images.unsplash.com/photo-1513104890138-7c749659a591?w=500&auto=format&fit=crop&q=60'
        },
        {
          id: 2,
          title: 'French Pastry & Macaron Secrets',
          chef: 'Amélie Laurent',
          category: 'Desserts',
          price: 920,
          rating: 4.8,
          description: 'Master the delicate art of meringue, piping consistent shells, and creating decadent ganache fillings.',
          image: 'https://images.unsplash.com/photo-1569864358642-9d1684040f43?w=500&auto=format&fit=crop&q=60'
        },
        {
          id: 3,
          title: 'Traditional Japanese Sushi Artistry',
          chef: 'Kenji Tanaka',
          category: 'Seafood',
          price: 850,
          rating: 5.0,
          description: 'Perfect your seasoned rice technique and master technical knife cuts for fresh sashimi and inside-out maki rolls.',
          image: 'https://images.unsplash.com/photo-1579871494447-9811cf80d66c?w=500&auto=format&fit=crop&q=60'
        },
        {
          id: 4,
          title: 'Gourmet Steakhouse Searing',
          chef: 'Marcus Visser',
          category: 'Grill',
          price: 1100,
          rating: 4.7,
          description: 'Understand meat selection, precision temperature management, pan-searing basting tricks, and rich reduction sauces.',
          image: 'https://images.unsplash.com/photo-1544025162-d76694265947?w=500&auto=format&fit=crop&q=60'
        }
      ]
    }
  },
  methods: {
    // Adds or removes an item ID from the wishlist array smoothly
    toggleWishlistHandler(courseId) {
      const position = this.wishlist.indexOf(courseId);
      if (position > -1) {
        this.wishlist.splice(position, 1); // Already exists? Remove it!
      } else {
        this.wishlist.push(courseId); // New item? Save it!
      }
    }
  }
}
</script>

<style>
/* Reset and App-Wide Global Layout Styles */
:root {
  --bg-color: #f9fbfd;
  --text-color: #2c3e50;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: var(--bg-color);
  color: var(--text-color);
  font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
}

.main-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
}

.hero-section {
  text-align: center;
  margin-bottom: 40px;
}

.hero-section h2 {
  font-size: 2rem;
  color: #2c3e50;
  margin-bottom: 8px;
}

.hero-section p {
  color: #7f8c8d;
  font-size: 1.1rem;
}

/* Flexbox/Grid responsive cards layout wrapper */
.catalog-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 30px;
}

@media (max-width: 480px) {
  .catalog-grid {
    grid-template-columns: 1fr; /* Flattens to single column on mobile layouts */
  }
}
</style>
