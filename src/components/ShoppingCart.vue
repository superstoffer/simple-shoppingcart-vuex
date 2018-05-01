<template>
  <div>
    <h1>Indkøbskurv</h1>
    <ul>
      <li v-for="product in products">
        {{ product.title }} - {{ product.price | currency }} - {{ product.quantity }}
      </li>
    </ul>
    <p>
      Total {{ total | currency  }}
    </p>
  </div>
</template>

<script>


  export default {
    name: "shopping-cart",
    computed: {
      products () {
        return this.$store.getters.cartProducts
      },
      total () {
        return this.$store.getters.cartTotal
      }
    }
  }
</script>

<style scoped>

</style>
