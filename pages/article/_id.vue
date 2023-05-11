<template>
<div class="container mx-auto p-6">
  <ProductDetail :productId="$route.params.id" />
</div>
</template>

<script>
export default {
  data() {
    return {
      productId: 1
    }
  }
}
</script>
