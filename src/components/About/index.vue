<template>
  <div>About {{productName}}</div>
</template>

<script>
  const products={
    1: 'shoes',
    11: 'pen',
    20: 'apple'
  }
  export default {
    data(){
      return{}
    },
    mounted() {
    },
    computed:{
      productName(){
        return products[this.$route.params.id]? products[this.$route.params.id]: 'Nothings'
      }
    }
  }
</script>