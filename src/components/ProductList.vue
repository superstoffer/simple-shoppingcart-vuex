<template>
  <div>
    <h1>Produkter</h1>
    <img
      v-if="loading"
      src="https://i.imgur.com/seuaOqf.gif"
      alt="Loading..."
    >
    <ul>
      <li v-for="product in products">
        {{ product.title }} - {{ product.price }}
        <button @click="addProductToCart(product)">Tilføj til kurv</button>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "product-list",
    data() {
      return {
        loading: false
      }
    },
    computed: {
      products () {
        return this.$store.getters.availableProducts
      }
    },
    methods: {
      addProductToCart (product) {
        this.$store.dispatch('addProductToCart', product)
      }
    },
    created () {
      this.loading = true
      this.$store.dispatch('fetchProducts')
        .then(() => this.loading = false)
    }
  }
</script>

<style scoped>

</style>
