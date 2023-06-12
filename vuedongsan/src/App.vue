<template>
  <div class="menu">
    <a v-for="(a,i) in 메뉴들" :key="i">{{a}}</a>
  </div>
  <div v-for="(a,i) in products" :key="i">
    <h4>{{ a }}</h4>
    <p>40 만원</p>
    <button @click="신고수[i]++">허위매물신고</button> <span>신고수: {{ 신고수[i] }}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      // 데이터 보관함
      // 데이터는 object 자료형으로 저장한다. {자료이름:자료내용}
      메뉴들: ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      신고수: [0, 0, 0],
    }
  },
  methods: {
    // 함수 만드는 공간
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{background:darkslateblue; padding:15px; border-radius:5px;}
.menu a{color:#fff; padding:10px;}
</style>
