<template>
  <div class="home">
    <ProductList @addProductToCart="addProductToCart"/>
    <ul>
            <li v-for="product in cart" :key='product.name'>
                {{product.name}}
            </li>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src
import ProductList from "@/components/ProductList"

export default {
  name: 'Home',
  components: {
    ProductList,
  },
  data(){
    return{
      cart: []
    }
  },
  methods: {
    addProductToCart(productName){
      this.cart.push({name: productName, number: 1})
    }
  }
}
</script>

<style scoped>
  
</style>