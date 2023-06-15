<template>

  <ModalDetail :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" />

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
import ModalDetail from './components/ModalDetail.vue';
import DiscountBanner from './components/DiscountBanner.vue';

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
    ModalDetail : ModalDetail,
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
</style>
