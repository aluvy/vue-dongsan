<template>

  <div v-if=" 1==2 ">
    안녕하세요
  </div>
  <div v-else>
    위에거가 참이 아니면 실행해주세요
  </div>

  
  <div class="black-bg" v-if="모달창열렸니==1">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" class="room-img">
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <p>{{ 원룸들[누른거].price }}</p>
      <button @click="모달창열렸니=0">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(a,i) in 메뉴들" :key="i">{{a}}</a>
  </div>

  <DiscountBanner />

  <div v-for="(a,i) in 원룸들" :key="i">
    <img :src="a.image" class="room-img">
    <h4 @click="모달창열렸니=1; 누른거=i;">{{ a.title }}</h4>
    <p>{{ a.content }}</p>
    <p>{{ a.price }}원</p>
  </div>

</template>

<script>
import data from './assets/oneroom';
import DiscountBanner from './DiscountBanner.vue';

export default {
  name: 'App',
  data(){
    return {
      메뉴들: ['Home', 'Shop', 'About'],
      모달창열렸니: 0,  // 0:닫힘, 1:열림
      원룸들: data,
      누른거: 0,
    }
  },
  methods: {
  },
  components: {
    DiscountBanner : DiscountBanner,
    // DiscountBanner,
  }
}
</script>

<style>
body {margin:0;}
div{box-sizing:border-box;}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{background:darkslateblue; padding:15px; border-radius:5px;}
.menu a{color:#fff; padding:10px;}

.room-img{width:100%; margin-top:40px;}

/* modal */
.black-bg{position:fixed; padding:20px; width:100%; height:100%; background:rgba(0,0,0, 0.5);}
.white-bg{width:100%; background:#fff; border-radius:8px; padding:20px;}
</style>
