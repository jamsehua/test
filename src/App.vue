<template>
  <div id="app">
    <div class="slideshow">
      <transition-group  class="item" name="hehe" tag="div">
        <!-- <div class="item" > -->
          <img :key="1" :src="dataList[currentindex]" alt="">
        <!-- </div> -->
      </transition-group>
      <div class="page">
        <ul>
          <li @click="preIndex" class="iconfont pre">&#xe74b;</li>
          <li></li>
          <li @click="nextIndex" class="iconfont next">&#xe627;</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>

  export default {
    name: 'App',
    components: {
    },
    data(){
      return {
        currentindex: 0,
        timer: null,
        dataList: ['https://aecpm.alicdn.com/simba/img/TB1XotJXQfb_uJkSnhJSuvdDVXa.jpg',
                   'https://aecpm.alicdn.com/simba/img/TB183NQapLM8KJjSZFBSutJHVXa.jpg',
                   'https://aecpm.alicdn.com/simba/img/TB1X6uHLVXXXXcCXVXXSutbFXXX.jpg',
                   '//img.alicdn.com/tfs/TB1kpdCx.T1gK0jSZFhXXaAtVXa-520-280.jpg_q90_.webp',
                   '//img.alicdn.com/tfs/TB10vWvxO_1gK0jSZFqXXcpaXXa-520-280.jpg_q90_.webp']
      }
    },
    methods: {
      preIndex(){
        if(this.currentindex == 0){
          return this.currentindex = this.dataList.length -1
        } else{
          this.currentindex --
        }
        console.log( this.currentindex)
      },
      nextIndex(){
        if(this.currentindex < 4){
          this.currentindex ++
        } else{
          this.currentindex = 0
        }
        console.log(this.currentindex)
      }
    },
    mounted(){
      this.timer = setInterval(() => {
        // this.nextIndex()
        this.currentindex ++
      }, 2500)
    }
  }
</script>

<style>
 @import 'assets/css/inconfont.css';
 @import 'assets/css/normalize.css';
 #app{
   position:fixed;
   top: 28%;
   left: 25%;
 }
 .iconfont{
    font-family:"iconfont" !important;
    font-size:16px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;
  }
  .slideshow{
    position: relative;
  }
 .item {
   width: 400px;
   height: 200px;
 }

 .item img{
   width: 100%;
   height: 100%;
 }

 .page li{
   cursor: pointer;
   position: absolute;
   top: 50%;
   font-size: 25px;
 }
 .pre{
   left: 5px;
 }
 .next{
   right: 5px;
 }
 
 .hehe-enter,.hehe-leave-to{
     opacity: 0;
 }
 .hehe-enter-to,.hehe-leave{
     opacity: 1;
 }
 .hehe-enter-active,.hehe-leave-active{
     transition: all 10s;
 }
</style>
