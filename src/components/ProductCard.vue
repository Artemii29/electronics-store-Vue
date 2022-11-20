<template>
  <div class="card">
    <img  :src="url+img" alt="">
    <h5>{{title}}</h5>
    <h4>{{price}}</h4>
    <button @click="$emit('add',id)">Купить</button>
  </div>
</template>

<script>
import {url} from "@/variables";
export default {
  name: "ProductCard",
  props:['id','img','title','price'],
  data(){
    return{
      url
    }
  }
}
</script>

<style scoped>
.card{
  width: 200px;
  padding: 15px;
  border: solid 1px #ccc;
  margin: 20px;
  text-align: center;
}
.card img{
  width: 100%;
  height: 120px;
  object-fit: contain;
}
</style>