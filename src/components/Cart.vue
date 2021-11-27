<template>
  <div class="body">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    <h1>Your Cart</h1>
    <h1 class="total"> Total: </h1>
    <div class="products">
      <div class="prod-card" v-for="(product, index) in cart" :key="index">
        <div class="card">
          <h3>{{product.name}}</h3>
          <img :src="product.img"  width="235px" height="140px"/>
          <div><b>Price: {{product.price}} </b></div>
          <div><b>Stock: {{product.quantity}}</b></div>
          <button type="button" class="btn btn-danger" v-on:click="removeItemFromCart(product)">Remove from Cart</button>
          <p>Value: {{ value }}</p>
           <vue-number-input v-model="value" :min="1" :max="10" inline controls></vue-number-input>
        </div>
        
      </div>
    </div>
    <div> </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
        value: 1,
    };
  },
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

.prod-card{
    float: left;
    width: 30%;
    padding: 0 10px;
}

.products {
    margin: 0 -5px;
    }
.products:after {
  content: "";
  display: table;
  clear: both;
}
.prod-name{
    padding-top: 20px;
}

.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2); /* this adds the "card" effect */
  padding: 16px;
  text-align: center;
  background-color: #f1f1f1;
}
.total{
 text-align: center;
}


</style>