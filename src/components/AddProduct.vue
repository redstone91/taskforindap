<template>
  <aside>
    <h2>Добавление товара</h2>
    <form ref="form">
        <p class="item">
            <label for="product-name">Наименование товара <span class="required"></span></label>
            <input type="text" name="product-name" placeholder="Введите наименование товара"   v-model.trim="product.name" :v="$v.product.name"  :class="{ hasError: $v.product.name.$error }"/>
            <span class="error-msg" v-if="$v.product.name.$error">Поле является обязательным</span>
        </p>
        <p class="item">
            <label for="product-desc">Описание товара</label>
            <textarea name="product-desc" placeholder="Введите описание товара" v-model="product.desc"></textarea>
        </p>
        <p class="item" >
            <label for="product-link" >Ссылка на изображение товара <span class="required"></span></label>
            <input type="text" name="product-link" placeholder="Введите ссылку"   v-model.trim="product.cover" :v="$v.product.cover"  :class="{ hasError: $v.product.cover.$error }"/>
            <span class="error-msg" v-if="$v.product.cover.$error">Поле является обязательным</span>
        </p>
        <p class="item">
            <label for="product-price" >Цена товара <span class="required"></span></label>
            <input type="text" name="product-price" placeholder="Введите цену" v-model.trim="product.price" :v="$v.product.price"  :class="{ hasError: $v.product.price.$error }"/>
            <span class="error-msg" v-if="$v.product.price.$error">Поле является обязательным</span>
        </p>
        <p class="item">
            <button :class="{success: success}" @click="addProduct">Добавить товар</button>
        </p>
    </form>
  </aside>

</template>

<style scoped>


aside{
  padding: 32px 8px 32px 32px;
}

h2{
  font-style: normal;
  font-weight: 600;
  font-size: 28px;
  line-height: 35px;
  color: #3F3F3F;
  margin: 0;
  padding-bottom: 16px;
}

form{
  width: 332px;
  min-height: 440px;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 24px;
}

label{
  font-style: normal;
  font-weight: normal;
  font-size: 10px;
  line-height: 13px;
  letter-spacing: -0.02em;
  color: #49485E;
}

p.item{
  display: flex;
  flex-direction: column;
  margin-bottom: 16px;
  position: relative;
}

input, textarea{
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  padding: 10px 16px;
  outline: 0;
  border: 0;
  border: 1px solid transparent;
  color: #3F3F3F;
  font-size: 12px;
}
input::placeholder,
textarea::placeholder{
  font-size: 12px;
  line-height: 15px;

  color: #B4B4B4
}
textarea{
  resize: none;
  height: 108px;
}
label{
  position: relative;
  padding-bottom: 4px;
}

.required{
  background: #FF8484;
  border-radius: 50%;
  width: 5px;
  height: 5px;
  margin-left: 2px; 
  display: inline-flex;
  margin-bottom: 5px;
}

button{
  border: unset;
  cursor: pointer;
  background: #EEEEEE;
  border-radius: 10px;
  width: 100%;
  height: 36px;
  margin-top: 8px;
  user-select: none;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  color: #B4B4B4;
}

button:hover{
  background-color: rgba(0, 0, 0, 0.1);
}
button.success:hover,
.success{
  background: #7BAE73;
  color: #FFFFFF;
}

.hasError{
  border: 1px solid #FF8484;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}
.error-msg{
  font-size: 8px;
  line-height: 10px;
  letter-spacing: -0.02em;
  color: #FF8484;
  padding-top: 4px;

}
</style>

<script>
import { required } from "vuelidate/lib/validators";

export default {
  name: 'AddProduct',
  props: ['products'],
  data (){
    return {
      product: {
        name: null,
        cover: null,
        desc: null,
        price: null
      },
      success: false
    }
  },
  validations: {
    product: {
      name: { 
        required
      },
      cover: { 
        required
      },
      //desc: { required },
      price: {
       required
     }

    }
  },
  methods: {
    addProduct (e){
      e.preventDefault();
      this.$v.product.$touch();
      if (this.$v.product.$pending || this.$v.product.$error) return;
      this.products.push({...this.product});
      this.success = true;
      setTimeout(this.reset, 1500)
    },
    reset(){

      this.success = false;
      this.product.name = null;
      this.product.cover = null;
      this.product.desc = null;
      this.product.price =  null;
      this.$v.product.name.$reset();
      this.$v.product.cover.$reset();
      this.$v.product.price.$reset();

    } 
  }
}
</script>
