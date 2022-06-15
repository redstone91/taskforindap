<template>
  <aside class="products">
      <div class="filter__wrapper">
        <ProductFilter/>
      </div>
      <div class="products__wrapper">
          <Card :product="product" :index="i" v-for="(product, i) in products" :key="i"/>
      </div>
  </aside>

</template>

<style scoped>

aside{
  padding: 0px 8px 16px 0;


  flex-direction: column;
}
.filter__wrapper{
  display: flex;
  justify-content: flex-end;
  padding: 31px 26px 8px 0;

}

.products__wrapper{
  display: flex;
  flex-wrap: wrap;
}

.products__wrapper > div{
  margin: 8px;

}

</style>

<script>
import Card from './Card.vue';
import ProductFilter from './ProductFilter.vue';
export default {
  name: 'Products',
  components: { Card, ProductFilter },
  props: ['products'],

  data (){
    return {

    }
  },
  mounted (){
    this.$root.$on('delete', index=>{
        this.products.splice(index, 1);
    })
  }
}
</script>
