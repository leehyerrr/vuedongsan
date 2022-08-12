<template>
    <div class="black-bg" v-if="openModal" >
    <div class="white-bg">
      <h4>{{oneroom[idx].title}}</h4>
      <img :src="oneroom[idx].image">
      <p>{{oneroom[idx].content}}</p>
      <p>{{oneroom[idx].price}}</p>
      <p>{{object.name}}</p>
      <button @click="modal">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name:"Modal",
    props:{
      openModal:Boolean,
      oneroom:Array,
      modal:Function,
      idx:Number,
      object:Object
    }
}
</script>

<style>

</style>