<template>
  <div>
    <div class="relative group bg-white dark:bg-gray-900 text-gray-700 dark:text-gray-300">
      <div class="product-card-content">
        <a
          href="/product/maionez-heinz-klassiceskii-67-1"
          class="inline-block w-full relative lg:rounded-md rounded-t-md p-3 lg:shadow-md"
          ><div
            class="w-full bg-contain bg-center bg-no-repeat bg-blend-multiply sm:h-56 h-52 bg-gray-100 dark:bg-gray-300 rounded-md overflow-hidden group-hover:opacity-75 lg:h-72 xl:h-56"
            :style="{ backgroundImage: `url(https://app.mototaxi.tj/${product.images[0]})` }"
          ></div>
          <h3 class="mt-1 sm:text-sm text-xs line-clamp-1 font-semibold">
            {{ product.title }}
          </h3>
          <p class="mt-1 sm:text-sm text-xs line-clamp-2 sm:h-10 h-8">
            {{ product.short_desc }}
          </p>
          <p class="mt-1 text-2xl font-medium">
            <span>{{ product.price }}</span>
            <!---->
            с.
          </p></a
        >
        <div
          class="lg:bg-gray-50 lg:dark:bg-gray-800 datk:bg-gray-900 dark:border-gray-900 border-t items-center justify-center lg:absolute bottom-0 w-full rounded-b-md lg:hidden flex lg:group-hover:flex lg:shadow-md"
        >
          <button
            type="button"
            @click="addToCart"
            class="bg-brand rounded-md text-sm px-4 py-2 my-2 hover:bg-red-600 text-white dark:text-gray-100"
          >
            Добавить в корзину
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      default: {}
    }
  },

  methods: {
    addToCart() {
      this.$emit('addToCart')
    }
  }
}
</script>
