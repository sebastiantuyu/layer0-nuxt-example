<script lang="ts">
import { getProductById, getApiPath } from '../../lib/cms'
import Rating from '../../components/Rating.vue'

export default {
  components: {
    Rating,
  },
  async asyncData({ params }: { params: any }) {
    const product = await getProductById(params.name)

    return { product }
  },
  methods: {
    getApiPath,
  },
}
</script>

<template>
  <div class="container center flex flex-col items-center md:flex-row pb-20">
    <div class="container p-5 flex flex-col items-center">
      <img :src="product.picture" :alt="product.name" />
    </div>
    <div class="container p-5 flex flex-col items-center md:items-start text-center md:text-left">
      <h2 class="font-bold py-2 m2">{{ product.name }}</h2>
      <div class="py-2 m2">{{ product.description }}</div>
      <div class="py-2 m2">${{ product.price }}</div>
      <div class="py-2 m2">
        <Rating :value="Number(product.rating)" />
      </div>
      <div class="py-2 m2">
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
          Add To Cart
        </button>
      </div>
    </div>
  </div>
</template>
