<template>
  <div class="black-bg" v-if="모달창열렸니==1">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="모달창열렸니=0">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(a,i) in 메뉴들" :key="i">{{a}}</a>
  </div>

  <div v-for="(a,i) in products" :key="i">
    <img :src="require(`@/assets/room${i}.jpg`)" class="room-img">
    <h4 @click="모달창열렸니=1">{{ a }}</h4>
    <p>40 만원</p>
    <button @click="신고수[i]++">허위매물신고</button> <span>신고수: {{ 신고수[i] }}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      메뉴들: ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      신고수: [0, 0, 0],
      모달창열렸니: 0,  // 0:닫힘, 1:열림
    }
  },
  methods: {
  },
  components: {
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
