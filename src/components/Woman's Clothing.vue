<template>
  <div class="product-list">
    <ProductSection v-for="product in products" :key="product.id" :product="product" />
    <button @click="fetchNextProduct" :disabled="isLastProduct">Next Product</button>
  </div>
</template>

<script>
import ProductSection from '@/components/ProductSection.vue';

export default {
  components: {
    ProductSection,
  },
  data() {
    return {
      products: [],
      index: 1,
    };
  },
  computed: {
    isLastProduct() {
      return this.index === 20;
    },
  },
  methods: {
    async fetchNextProduct() {
      if (this.index < 20) {
        const response = await fetch(`https://fakestoreapi.com/products/${this.index}`);
        const data = await response.json();
        if (data.category === 'men's clothing' || data.category === 'women's clothing') {
          this.products.push(data);
          this.index++;
        } else {
          this.index++;
          this.fetchNextProduct();
        }
      } else {
        this.index = 1;
      }
    }
  }
  mounted() {
    this.fetchNextProduct();
  }
}
</script>

<style scoped>
.product-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin: 20px 0;
}

.product-list button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: var(--color-secondary); /* Updated to use the correct variable name */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

.product-list button:hover {
  background-color: var(--color-primary); /* Updated to use the correct variable name */
}

.product-list button:disabled {
  background-color: var(--color-septenary); /* Updated to use the correct variable name */
  cursor: not-allowed;
}
</style>
