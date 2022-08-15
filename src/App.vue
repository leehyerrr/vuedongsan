<template>

<!--class문법 <div class="start" :class="{end:openModal}">
  <Modal :oneroom=oneroom :modal=modal :openModal=openModal :idx=idx :object=object @emitModal="modal"/>
</div> -->

<!-- vue transtion문법 -->
<transition name="fade">
    <Modal :oneroom=oneroom :modal=modal :openModal=openModal :idx=idx :object=object @emitModal="modal"/>
</transition>


  <div class="menu">
    <a v-for="(x,i) in menus" :key="i">{{x}}</a>
  </div>

  <discount :showDiscount=showDiscount />
  <button @click="orderPrice">가격순 버튼</button>
  <button @click="orderPrice2">가격역순 버튼</button>
  <!-- <button @click="orderPrice3">가나다순 버튼</button> -->
  <button @click="orderPrice4">되돌리기</button>

  <!-- <Card :a=oneroom[0] />
  <Card :a=oneroom[1] />
  <Card :a=oneroom[3] />
  <Card :a=oneroom[4] />
  <Card :a=oneroom[5] /> -->

  <Card @openModal2="modal" :a=oneroom[i] v-for="(x,i) in oneroom" :key="i"/>


</template>

<script>
import oneroom from './assets/oneroom';
import discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  data(){
    return{
      // pop:"pop",
      object : {name:"kim", age:30},
      oneroom: oneroom,
      oneroomCopy : [...oneroom],
      products:['역삼동원룸','천호동원룸','마포구동원룸'],
      menus : ['home','about','shop'],
      declation: [0,0,0],
      openModal : false,
      idx : 0,
      showDiscount:30
      // array : oneroom.title,
    }
  },
  methods: {
    modal(i){
      // console.log(this[i]);
      if(this.openModal == false) {
        return this.openModal = true, this.idx = i; 
        } 
        else {return this.openModal = false}
      // this.idx = i;
      // this.press = i
      // return this.openModal = true;
    },
    orderPrice(){
      this.oneroom.sort(function(a,b){
        return a.price - b.price
      })
    },
    orderPrice2(){
      this.oneroom.sort(function(a,b){
        return b.price - a.price
      })
    },
    // orderPrice3(){
    //   console.log(this.array)
    //   // var array;
    //   for(let i=0; i<this.oneroom.length; i++){
    //     this.array.push(this.oneroom[i].title)
    //     // console.log(this.oneroom[i].title)
    //     };
    //   console.log(this.array);
    //   this.array.sort();
    // }, 
    orderPrice3(){
      this.oneroom.sort(function(a,b){
        return b.title - a.title
      })
    },
    orderPrice4(){
      this.oneroom = [...this.oneroomCopy]
    }      
  },
  mounted(){
    setInterval(()=>{
      this.showDiscount -= 1
    },1000)
  },
  components: {
    discount : discount,
    Modal : Modal,
    Card : Card,
  }
}
</script>

<style>
html {padding:0px; margin:0}
body {padding:0px;margin:0}
div {box-sizing: border-box;}
.black-bg {width:100%; height:100%; position:fixed; padding:20px; background:rgba(0,0,0,0.5)}
.white-bg {font-size:15px; width:100%; background:white; border-radius: 8px; padding:20px}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.sect {margin-bottom:30px}
.menu {background:darkblue; padding:15px; border-radius: 15px;}
.menu a {color:#fff; padding:10px}

img {width:100%}

.start {opacity: 0; transition: all 1s;}
.end {opacity: 1;}

/* 입장 animation */
.fade-enter-from {opacity: 0; transform:translate(0,-200px);}
.fade-enter-active{transition: all 1s;}
.fade-enter-to{opacity: 1;transform:translate(0,0px);}
/* 퇴장 animation */
.fade-leave-from {opacity: 1;}
.fade-leave-active{transition: all 1s;}
.fade-leave-to{opacity: 0;}
</style>