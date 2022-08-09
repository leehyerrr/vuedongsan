<template>
    <div class="black-bg" v-if="openModal" >
      <div class="white-bg">
        <h4>{{oneroom[i].title}}</h4>
        <p>내용임</p>
        <button @click="modal">닫기</button>
      </div>
    </div>


  <div class="menu">
    <a v-for="(x,i) in menus" :key="i">{{x}}</a>
  </div>

  <div class="sect" v-for="(a,i) in oneroom" :key="i">
    <img :src="a.image">
    <h4 @click="modal">{{a.title}}</h4>
    <p>{{a.price}}</p>
  </div>    
</template>

<script>
import oneroom from './assets/oneroom';

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
      press : 0,
    }
  },
  methods: {
    modal(){
      // console.log(this[i]);
      if(this.openModal == false) {return this.openModal = true} else {return this.openModal = false}
      // this.press = i
      // return this.openModal = true;
    }
  },
  components: {
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