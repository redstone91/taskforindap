<template>

<main>
  <AddProduct :products="products"/>
  <Products :products="products"/>
</main>

</template>

<style scoped>
  
main{
  width: 1440px;
  height: 900px;
  background: rgba(255, 254, 251, 0.8);
  display: flex;
}

</style>

<script>
import AddProduct from './components/AddProduct.vue';
import Products from './components/Products.vue';

/*

*/
export default {
  name: 'App',
  components: { AddProduct, Products},
  data (){
    return {
      products: []
    }
  },
  created (){
    this.getProducts();
  },

  methods: {
    async getProducts (){
        fetch('products.json')
            .then(res=>res.json())
            .then(res=>{
                this.products = res;
            })
    }
  }
}
</script>