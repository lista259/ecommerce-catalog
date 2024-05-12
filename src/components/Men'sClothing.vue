<template>
  <div class="product-section" :class="productCategoryClass">
    <figure class="product-image">
      <img :src="men-section.png" alt="Men's Clothing">
    </figure>
    <div class="product-description">
      <h2 :class="productCategoryClass">{{ product.category }}</h2>
      <p v-if="product.description" v-html="product.description"></p>
      <p v-else>great outerwear jackets for Spring/Autumn/Winter, suitable for many occasions, such as working, hiking, camping, mountain/rock climbing, 
        cycling, traveling or other outdoors. Good gift choice for you or your family member. A warm hearted love to Father, 
        husband or son in this thanksgiving or Christmas Day.</p>
      <p class="product-price">$29.95</p>
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
      <!-- Buy Now button -->
      <button class="buy-now">Buy Now</button>
      <!-- Next Product button -->
      <button class="next-product">Next Product</button>
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
    },
    isWoman() {
      return this.product.category === 'Women’s Clothing';
    },
    isMan() {
      return this.product.category === 'Men’s Clothing';
    }
  }
};
</script>

<style scoped>
.customButtonWoman button, .customButtonMan button {
    font-family: "Prompt", sans-serif;
    color: white;
    padding: 10px;
    margin-right: 20px;
    margin-top: 20px;
    width: 90%;
    border-radius: 5px;
}

.customButtonWoman button {
    border: 2px solid #720060;
    background-color: #720060;
}

.customButtonMan button {
    border: 2px solid #002772;
    background-color: #002772;
}

.product-price {
    font-size: 18px;
    color: #333;
    font-weight: bold;
    margin-top: 10px;
}

.buy-now, .next-product {
    font-size: 16px;
    padding: 10px 20px;
    margin-top: 10px;
    border-radius: 5px;
    cursor: pointer;
    outline: none;
    border: none;
}

.buy-now {
    background-color: #4CAF50; /* Green */
    color: white;
}

.next-product {
    background-color: #008CBA; /* Blue */
    color: white;
}
</style>
