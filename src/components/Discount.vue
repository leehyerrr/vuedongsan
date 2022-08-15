<template>
  {{showDiscount}}
</template>

<script>
export default {
    name: 'discount',
    props:{
      showDiscount:Number
      }    
    }
</script>

<style>
.discount {padding:10px; background:gray}
</style>