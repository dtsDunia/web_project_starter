<template>
<div class="bg-gray-100">
  <div class="flex flex-col justify-between h-full w-full min-h-128">
    <div class="flex flex-col justify-center items-center md:flex-row md:items-start space-y-8 md:space-y-0 md:space-x-4 lg:space-x-8 max-w-6xl w-11/12 mx-auto">
      <div class="w-full md:w-1/2 max-w-md border border-gray-200 bg-white rounded shadow-lg">
        <div class="relative h-96">
          <img :src="product.thumbnail" alt="some alt text" layout="fill" class="transform duration-500 ease-in-out hover:scale-105" />
        </div>
        <div class="relative flex border-t border-gray-200">
          <button aria-label="left-scroll" class="h-32 bg-gray-200 hover:bg-gray-400  absolute left-0 z-10 opacity-75"></button>
          <div class="flex space-x-1 w-full overflow-auto border-t border-gray-200">
            <button class="relative w-40 h-32 flex-shrink-0 rounded-sm"></button>
          </div>
          <button aria-label="right-scroll" class="h-32 bg-gray-200 hover:bg-gray-400  absolute right-0 z-10 opacity-75"></button>
        </div>
      </div>
      <div class="">
        <h1 class="leading-relaxed font-extrabold text-3xl">
          {{ product.title }}
        </h1>
        <p class="font-medium text-lg">
          {{ product.description }}
        </p>
        <div v-if="product.price" class="text-2xl font-medium py-4 px-1 text-right">
          Rp {{ product.price }}
        </div>
      </div>

      <div class="w-full">
        <div class="flex justify-start space-x-2 w-full">
          <div class="flex flex-col items-start flex-grow-0">
            <label class="text-gray-500 text-base mb-2">Qty.</label>
            <input type="text" name="quantity" min="1" step="1" class="border border-gray-500 w-16 rounded focus:border-purple-500 focus:ring-purple-500 p-2">
          </div>
          <div class="flex flex-col w-full">
            <label class="text-gray-500 text-base mb-2">Size</label>
            <div class="relative">
              <button v-click-outside="closeDropdown" type="button" class="w-full border border-gray-300 bg-gray-300 focus:bg-gray-400 hover:bg-gray-400 rounded p-2" @click.stop="toggleDropdown">
                Some dropdown
              </button>
              <div class="absolute bottom-0 translate-y-full w-full ">
                <ul v-show="dropdownVisible" class="cursor-pointer border mt-1 bg-gray-100 block z-50">
                  <li class="hover:bg-gray-300 focus:bg-gray-300 border-b p-3">Lorem ipsum</li>
                  <li class="hover:bg-gray-300 focus:bg-gray-300 border-b p-3">Lorem ipsum dolor sit</li>
                  <li class="hover:bg-gray-300 focus:bg-gray-300 p-3">Lorem ipsum dolor</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
        <div class="">
          <a class="pt-3 pb-2 bg-purple-500 text-white w-full mt-2 rounded-sm font-primary text-xl flex justify-center items-baseline hover:bg-purple-600 cursor-pointer">
            Add To Cart
          </a>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      product: {},
      dropdownVisible: false
    }
  },
  mounted() {
    this.getProduct(this.productId)
  },
  props: [
    'productId'
  ],
  methods: {
    toggleDropdown(event) {
      this.dropdownVisible = !this.dropdownVisible
    },
    closeDropdown() {
      this.dropdownVisible = false
    },
    async getProduct(id) {
      await fetch(`https://dummyjson.com/products/${id}`)
        .then(response => response.json())
        .then(data => this.product = data)
    }
  }
}
</script>
