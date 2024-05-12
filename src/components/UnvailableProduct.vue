<template>
  <div :class="productCategoryClass">
    <!-- Product information goes here -->
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
      return this.product.category === 'Unavailable Product' ? 'product-unavailable' : 'product-available';
    }
  }
}
</script>
