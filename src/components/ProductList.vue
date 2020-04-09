<template>
  <div>
    <h1>Product List</h1>
    <ul>
      <li v-for="product in products" :key="product.id">{{ product.title }}-{{ product.price }}</li>
    </ul>
  </div>
</template>

<script>
import shop from '@/api/shop'

export default {
  computed: {
    products() {
      return this.$store.getters.availableProducts
    }
  },

  created() {
    shop.getProducts(products => {
      this.$store.commit('setProducts', products)
    })
  }
}
</script>
