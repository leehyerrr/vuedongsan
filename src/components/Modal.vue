<template>
    <div class="black-bg" v-if="openModal" >
    <div class="white-bg">
      <h4>{{oneroom[idx].title}}</h4>
      <img :src="oneroom[idx].image">
      <p>{{oneroom[idx].content}}</p>
      <p>{{oneroom[idx].price}}</p>
      <p>{{object.name}}</p>
      
      <p>선택한 개월수 : {{month}}</p>
      <p>가격: {{month*oneroom[idx].price}}</p>
      <p><input type="text" @change="month = $event.target.value"></p>
      <p><input v-model="month"></p> <!-- 위에거랑 똑같음 -->
      <!-- v-model이라는것은 form마다 다르게 동작함, 다해보거라 -->
      <!-- <button @click="modal">닫기</button> -->
      <select v-model="selval">
        <option>11</option>
        <option>22</option>
        <option>33</option>
      </select>
      <input type="checkbox" v-model="chkval"> 아이구야
      <p>sel: {{selval}} chk: {{chkval}}</p>
      <button @click="$emit('emitModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name:"Modal",
    data(){
      return{
        month:0,// 초기값의 타입에 따라 적용이 되고 안되고 갈림,
        selval:3,
        chkval:true
      }
    },
    props:{
      openModal:Boolean,
      oneroom:Array,
      // modal:Function,
      idx:Number,
      object:Object
    }
}
</script>

<style>

</style>