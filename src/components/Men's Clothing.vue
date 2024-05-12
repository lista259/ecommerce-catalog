<template>
  <div class="product-section" :class="productCategoryClass">
    <figure class="product-image">
      <img :src="men-section.png" alt="Men's Clothing">
    </figure>
    <div class="product-description">
      <h2 :class="productCategoryClass">{{ product.category }}</h2>
      <p v-if="product.description" v-html="product.description"></p>
      <p v-else>No description available</p>
      <div class="categories">
        <button
          v-for="category in product.categories"
          :key="category"
          :class="category"
        >
          {{ category }}
        </button>
      </div>
      <div class="rating">{{ productRating }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      required: true
    }
  },
  computed: {
    productCategoryClass() {
      if (this.product.category === 'Men’s Clothing') {
        return 'men';
      } else if (this.product.category === 'Women’s Clothing') {
        return 'women';
      } else {
        return 'unavailable';
      }
    },
    productRating() {
      return this.product.rating.toFixed(1);
    }
  }
};
</script>
