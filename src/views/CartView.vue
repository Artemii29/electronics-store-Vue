<template>
<h1>Card page</h1>
  <div class="allcard">
  <ProductCardDel v-for="item in carts" :key="item.id" :title="item.title" :price="item.price" :img="item.img" :id="item.id" @del="delCart"/>


  </div>
</template>

<script>
import ProductCardDel from "@/components/ProductCardDelete";
import {url} from "@/variables";
export default {
  components: {ProductCardDel},
  data() {
    return {
      carts: [],
      url
    }
  },
  methods: {
    delCart(id) {
      console.log(id)
      let result = this.carts.find((elem) => elem.id === id)
      let index = this.carts.indexOf(result)
      this.carts.splice(index, 1)
    }

  },
  mounted() {
    console.log(localStorage.getItem('cart'))
    try {
      this.carts = JSON.parse(localStorage.getItem('cart'))
    } catch (err) {
      this.carts = []
    }
  }
}


</script>
<style>
.allcard{
  display: flex;
  padding: 30px;
  box-sizing: border-box;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>