<template>
  <h1>Home page</h1>
  <quiksearch/>
  <div>
    <VSelect :categories="categories" :dat="data" @onSelected="(item) => selectedCategory = item"
    />
  </div>
  <div class="product_list">
    <ProductCard v-for="item in computedData" :key="item.id" :title="item.title" :price="item.price" :img="item.img"
                 :id="item.id" @add="addCart"/>

  </div>
</template>
<script>
import {data} from "@/variables";
import VSelect from "@/components/VSelect";
import ProductCard from "@/components/ProductCard";
import quiksearch from "@/components/quikSearch";

export default {
  components: {quiksearch, ProductCard, VSelect},
  data() {
    return {
      data,
      cart: [],
      categories: [

        {c_id: 1, category: 'Смартфоны'},
        {c_id: 2, category: 'Ноутбуки'},
        {c_id: 3, category: 'Телевизоры'}
      ],
      selectedCategory: ""

    }
  },
  computed: {
    computedData() {
      if(this.selectedCategory) {
        return this.data.filter(item => item.c_id === this.selectedCategory)
      }

        return this.data

    }
  },
  mounted() {
    console.log(localStorage.getItem('cart'))

    try {
      this.cart = JSON.parse(localStorage.getItem('cart'))
    } catch (err) {
      this.cart = []
    }
  },
  methods: {
    addCart(product_id) {
      let result = this.data.find((elem) => elem.id === product_id)
      let exist = this.cart.find((elem) => elem.id === product_id)
      if (exist) {
        exist.count++
      } else {
        result.count = 1
        this.cart.push(result)
      }
      localStorage.setItem('cart', JSON.stringify(this.cart))
      alert(`${result.title} add cart success!!!!`)
    },
  },
}
</script>
<style>
.product_list {
  display: flex;
  padding: 30px;
  box-sizing: border-box;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>