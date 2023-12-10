<script>
import axios from 'axios'
import Loading from '@/components/Loading.vue'
import ProductCard from '@/components/ProductCard.vue'
export default {
  components: {
    Loading,
    ProductCard
  },
  data() {
    return {
      products: [],
      loading: true,
      counter: 0
    }
  },

  mounted() {
    this.init()
  },

  methods: {
    init() {
      axios
        .get('https://app.mototaxi.tj/api/products?name=&page=1&city_id=1&sort_by=newest')
        .then((res) => {
          this.products = res.data.data
          this.loading = false
        })
        .catch((err) => {
          console.log('error', err)
          this.loading = false
        })
    },

    addToCardFromProductCard() {
      this.counter++
    }
  }
}
</script>

<template>
  <main class="container mx-auto">
    <div class="flex justify-between items-center py-28">
      <h1 class="text-3xl">Продукты</h1>
      <div class="text-3xl">{{ counter }} шт.</div>
    </div>
    <Loading v-if="loading" />
    <div v-else class="grid sm:gap-4 gap-2 grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
      <ProductCard
        v-for="product in products"
        :key="product.id"
        :product="product"
        @addToCart="addToCardFromProductCard"
      />
    </div>
  </main>
</template>
