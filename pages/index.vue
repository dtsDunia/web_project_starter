<template>
<div class="container mx-auto p-6">
  <ul class="grid grid-flow-cols grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-x-4 gap-y-8">
    <li v-for="product in products" :key="product.id">
      <Products :product="product" />
    </li>
  </ul>
</div>
</template>

<script>
export default {
  data() {
    return {
      products: []
    }
  },
  mounted() {
    this.getProducts()
  },
  methods: {
    async getProducts() {
      fetch('https://dummyjson.com/products')
        .then(response => response.json())
        .then(data => this.products = data.products)
    }
  }
}
</script>
