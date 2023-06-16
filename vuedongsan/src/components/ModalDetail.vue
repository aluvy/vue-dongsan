<template>
  <div class="modal_wrap black-bg" v-if="모달창열렸니==1">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" class="room-img">
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <div>개월 수 : <input type="text" v-model.number="month"></div>
      <p>[{{month}}개월 선택] {{ 원룸들[누른거].price * month }}원</p>
      <button @click="closeModal">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalDetail',
  data(){
    return {
      month: 1,
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
  }
}
</script>

<style>
/* modal */
.modal_wrap{position:fixed; padding:20px; width:100%; height:100%; background:rgba(0,0,0, 0.5);}
.modal_wrap .white-bg{width:100%; background:#fff; border-radius:8px; padding:20px;}
.modal_wrap input{width:40px;}
</style>