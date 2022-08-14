<template>

  <Modal :oneroom=oneroom :modal=modal :openModal=openModal :idx=idx :object=object @emitModal="modal"/>

  <div class="menu">
    <a v-for="(x,i) in menus" :key="i">{{x}}</a>
  </div>

  <discount/>

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
      products:['역삼동원룸','천호동원룸','마포구동원룸'],
      menus : ['home','about','shop'],
      declation: [0,0,0],
      openModal : false,
      idx : 0,
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
    }
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
</style>