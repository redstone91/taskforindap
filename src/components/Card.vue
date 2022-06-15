
<template>
  <div class="card">
      <img class="del" src="icons/delete.svg" @click="deleteProduct">
      <div class="card__cover" :style="coverURL"></div>
      <div class="card__info">
          <h3>{{product.name}}</h3>
          <p class="card__desc">{{product.desc}}</p>
          <p class="card__price">{{product.price}} руб.</p>
      </div>
  </div>
</template>

<style scoped>
  
.card{
  width: 332px;
  height: 423px;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  position: relative;
  cursor: pointer;
}
.card .del{
  display: none;
  position: absolute;
  cursor: pointer;
  width: 32px;
  height: 32px;
  top: -8px;
  right: -8px;
}
.card:hover .del{
  display: block;
}
.card .del:hover{
    filter: brightness(95%);
}
.card__cover{
  width: 100%;
  height: 200px;
  border-radius: 4px 4px 0px 0px;
  background-color: gray;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
.card__info{
  padding: 16px 16px 24px 16px;
}
h3{
  margin: 0;
  padding-bottom: 16px;
  letter-spacing: 1px;
}
.card__desc{
  overflow: hidden;
  height: 80px;
  font-size: 16px;
  line-height: 20px;
  color: #3F3F3F;
}
.card__price{
  font-style: normal;
  font-weight: 600;
  font-size: 24px;
  line-height: 30px;
  color: #3F3F3F;
  padding-top: 32px;

}
</style>

<script>

export default {
  name: 'Card',
  props: ['product', 'index'],
  computed: {
    coverURL (){
      return `background-image: url(${this.product.cover})`
    }
  },
  methods: {
    deleteProduct (){
      this.$root.$emit('delete', this.index)
    }
  }
}

</script>
