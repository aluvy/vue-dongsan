<template>

  <ModalDetail :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" @closeModal="모달창열렸니=0;" />

  <div class="menu">
    <a v-for="(a,i) in 메뉴들" :key="i">{{a}}</a>
  </div>

  <DiscountBanner v-if="showDiscountBanner == true" />

  <button type="button" @click="sortBack">전체</button>
  <button type="button" @click="priceSortDesc">가격 내림차순 정렬</button>
  <button type="button" @click="priceSortAsc">가격 오름차순 정렬</button>
  <button type="button" @click="ProductSort">가나다순 정렬</button>
  

  <ProductCard @openModal="모달창열렸니=1; 누른거=$event;" v-for="(a,i) in 원룸들" :key="i" :원룸="원룸들[i]" />

</template>

<script>
import data from './assets/oneroom';
import ModalDetail from './components/ModalDetail.vue';
import DiscountBanner from './components/DiscountBanner.vue';
import ProductCard from './components/ProductCard.vue';

export default {
  name: 'App',
  data(){
    return {
      오브젝트: {name: 'kim', age: 20},
      메뉴들: ['Home', 'Shop', 'About'],
      모달창열렸니: 0,  // 0:닫힘, 1:열림
      원룸들오리지널: [...data],
      원룸들: data,
      누른거: 0,
      showDiscountBanner: true,
    }
  },
  methods: {
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    },
    priceSortDesc(){
      this.원룸들.sort(function(a,b){
        return a.price - b.price;
      });
    },
    priceSortAsc(){
      this.원룸들.sort(function(a,b){
        return b.price - a.price;
      });
    },
    ProductSort(){
      this.원룸들.sort(function(a, b){
        if(a.title.toLowerCase() > b.title.toLowerCase())       return 1;
        else if(a.title.toLowerCase() < b.title.toLowerCase())  return -1;
        else  return 0;
      });
    }
  },

  // App.vue 가 mount 되었을 때 실행
  mounted(){
    setTimeout(() => {
      this.showDiscountBanner = false;
    }, 3000);
  },

  components: {
    DiscountBanner : DiscountBanner,
    ModalDetail : ModalDetail,
    ProductCard : ProductCard,
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

.menu{background:darkslateblue; padding:15px;}
.menu a{color:#fff; padding:10px;}

.room-img{width:100%; margin-top:40px;}
</style>
