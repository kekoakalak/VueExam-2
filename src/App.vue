<template>
  <div>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <header>
      <button class="btn btn-success" v-on:click="navigateTo('products')">View Products</button>
      {{cart.length}} in cart
      <button class="btn btn-success" v-on:click="navigateTo('cart')">View Cart</button>
      <button  class="btn btn-success" v-on:click="navigateTo('itemdetail')">Item Detail</button>
    
  
    </header>

    <div v-if="page === 'cart'">
      <Cart v-on:removeItemFromCart="removeItemFromCart" :cart="cart" />
    </div>

    <div v-if="page === 'products'">
      <Products v-on:addItemToCart="addItemToCart" />
    </div>

    <div v-if="page === 'itemdetail'">
      <ItemDetail v-on:removeItemFromCart="removeItemFromCart" :cart="cart"  />
    </div>

  </div>
</template>

<script>
import Products from "./components/Products.vue";
import Cart from "./components/Cart.vue";
import ItemDetail from "./components/ItemDetail.vue";
export default {
  name: "App",
  data: () => {
    return {
      page: "products",
      cart: []
    };
  },
  methods: {
    addItemToCart(product) {
      this.cart.push(product);
    },
    removeItemFromCart(product) {
      this.cart.splice(this.cart.indexOf(product), 1);
    },
    navigateTo(page) {
      this.page = page;
    }
  },
  components: { Products, Cart, ItemDetail }
};
</script>

<style>
body {
  margin: 0;
}
.products {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.products button {
  padding: 10px;
  color: white;
  outline: none;
  border: none;
  cursor: pointer;
}
</style>

<style scoped>
header {
  height: 80px;
  background-color:darkslateblue;
  text-align: right;
  font-size: 30px;
  padding-top: 20px;
}
header button {
  border: none;
  cursor: pointer;
  color: white;
  
}
</style>