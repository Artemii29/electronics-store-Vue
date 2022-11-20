<template>

  <select v-model="selected">
    <option  v-for="item in categories"  :value="item.c_id" :key="item.c_id" >{{item.category}}

    </option>

  </select>
</template>

<script>
export default {
  name: "VSelect",
  props:["categories",'dat'],
  emits:['onSelected'],
  data(){
      return{
        selected:''
      }
  },
  watch: {
    selected(newValue) {
      this.$emit('onSelected',newValue)
    }
  },
  // methods:{
  //   selectOption() {
  //    return this.dat.filter(item => item.c_id === this.selected.c_id)
  //   }
  // }
}
</script>

<style scoped>

</style>