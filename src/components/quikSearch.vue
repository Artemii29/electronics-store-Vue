<template>
  <input type="text" v-model="inpString">


  <div v-for="item in search" :key="item.id">
    {{item.title}}
  </div>

</template>

<script>
import {data} from '@/variables'
export default {
  name: "quikSearch",
  data(){
    return {
      data,
      inpString:''
    }
    },
  computed:{
    search(){
      if(this.inpString){
        console.log(this.inpString)
         return this.data.filter(item => item.title.toLowerCase().includes(this.inpString.toLowerCase()) )
      }
      else {
        return []
      }
    }
  }
}

</script>

<style scoped>

</style>