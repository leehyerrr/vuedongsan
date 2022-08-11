<template>

  <div class="black-bg" v-if="openModal" >
    <div class="white-bg">
      <h4>{{oneroom[idx].title}}</h4>
      <p>내용임ddddgd</p>
      <button @click="modal">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(x,i) in menus" :key="i">{{x}}</a>
  </div>

  <discount/>

  <div class="sect" v-for="(a,i) in oneroom" :key="i">
    <img :src="a.image">
    <h4 @click="modal(i)">{{a.title}}</h4>
    <p>{{i}}</p>
    <p>{{a.price}}</p>
  </div> 

</template>

<script>
import oneroom from './assets/oneroom';
import discount from './components/Discount.vue';

export default {
  name: 'App',
  data(){
    return{
      // pop:"pop",
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
    discount : discount
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