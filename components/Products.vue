<template>

<nuxt-link :to="`/article/${product.id}`" class="bg-gray-100 block border border-gray-400 rounded">
  <div class="border-b-1 border-palette-darker text-center pt-2">
    <img :src="product.thumbnail" alt="some alt text" layout="fill" class="inline w-auto h-48" />
  </div>
  <div class="bg-gray-200 p-3">
    <div class="h-52">
      <div class="font-primary text-2xl font-semibold mb-4">
        {{ product.title }}
      </div>
      <div class="text-lg text-gray-600 font-primary font-light">
        {{ truncate(product.description) }}
      </div>
    </div>
    <div class="text-right font-primary font-medium text-base triangle p-2">
      Rp{{ product.price }}
    </div>
  </div>

</nuxt-link>
</template>

<script>
export default {
  name: 'Tokoku',
  props: {
    product: {
      type: Object
    }
  },
  methods: {
    truncate(v) {
      const tl = this.product.title.length
      const sc = (this.product.title.match(/[A-Za-z0-9&#,+()$~%'":*?<>{}^]/mg) || []).length
      const kc = parseInt((100 * 30) / tl)
      const ad = !isNaN(parseFloat(sc)) && isFinite(sc) && sc > 70 ? parseInt(0) : kc
      const xd = kc > 150 ? (kc - sc) : ad

      return xd > 0 ? v.substring(0, xd) + '…' : ''
    }
  }
}
</script>
