<template>
  <div class="body">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <h1>Item Details</h1>
    <div class="products">
      <div class="prod-card" v-for="(product, index) in cart" :key="index">
        <div class="card">
          <h3>{{product.name}}</h3>
          <img :src="product.img"  width="235px" height="140px"/>
          <div><b>Price: {{product.price}} </b></div>
          <div><b>Stock: {{product.quantity}}</b></div>
          <div><b>Category: {{product.category[0]}}, {{product.category[1]}} </b></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["cart"],
  methods: {
    removeItemFromCart(product) {
      this.$emit("removeItemFromCart", product);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

.body{
   
    background-color: aliceblue;
}

.products{
    align-items: center;
    background-color: aliceblue;
}

.prod-card{
    margin: 20px 20px;
    box-sizing: border-box;
    padding: 16px;
    width: 300px;
}

</style>