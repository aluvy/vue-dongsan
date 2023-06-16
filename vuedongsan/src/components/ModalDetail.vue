<template>
  <Transition name="fade">
    <div class="modal_wrap black-bg" v-if="모달창열렸니==1">
      <div class="white-bg">
        <img :src="원룸들[누른거].image" class="room-img">
        <h4>{{ 원룸들[누른거].title }}</h4>
        <p>{{ 원룸들[누른거].content }}</p>
        <div>개월 수 : <input type="text" v-model="month"></div>
        <p>[{{month}}개월 선택] {{ 원룸들[누른거].price * month }}원</p>
        <button @click="closeModal">닫기</button>
      </div>
    </div>
  </Transition>
</template>

<script>
export default {
  name: 'ModalDetail',
  data(){
    return {
      month: 1,
    }
  },
  watch: {
    month(a, b){  // 감시할 데이터 이름으로 함수를 만든다. (a:변경후 데이터, b:변경 전 데이터)
      console.log('watch month');
      if(a >= 13 ){
        alert("경고");
        this.month=b;
      }
      if( isNaN(a) ){
         alert("문자 입력 금지");
         this.month=b;
      }
    }
  },
  props: {
    원룸들: Object, // Number, String, Array
    누른거: Number,
    모달창열렸니: Number,
  },
  methods: {
    closeModal(){
      this.$emit('closeModal');
    }
  },
  beforeUpdate(){
    if (this.month <= 2){
      alert('2개월은 너무 적음.. 안팝니다');
      this.month = 3;
    }
  },
}
</script>

<style>
/* modal */
.modal_wrap{position:fixed; padding:20px; width:100%; height:100%; background:rgba(0,0,0, 0.5);}
.modal_wrap .white-bg{width:100%; background:#fff; border-radius:8px; padding:20px;}
.modal_wrap input{width:40px;}


.fade-enter-from{opacity:0;}
.fade-enter-active{transition:all .3s;}
.fade-enter-to{opacity:1;}

.fade-leave-from{opacity:1;}
.fade-leave-active{transition:all .3s;}
.fade-leave-to{opacity:0;}
</style>