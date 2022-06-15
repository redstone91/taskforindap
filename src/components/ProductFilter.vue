<template>
  
  <div class="filter">
      <p>
          <span>По умолчанию</span>
          <img src="icons/arraw-down.svg">
      </p>
  </div>

</template>

<style scoped>

.filter{
  width: 121.49px;
  height: 36px;
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
.filter p span{
  font-size: 12px;
  line-height: 15px;
  color: #B4B4B4;
  padding-right: 5px;
}

</style>


<script>

export default {
  name: "ProductFilter"
}

</script>