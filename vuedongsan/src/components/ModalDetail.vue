<template>
  <div class="black-bg" v-if="모달창열렸니==1">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" class="room-img">
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <p>{{ 원룸들[누른거].price }}</p>
      <!-- <button @click="모달창열렸니=0">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalDetail',
  props: {
    원룸들: Object, // Number, String, Array
    누른거: Number,
    모달창열렸니: Number,
  }
}
</script>

<style>
/* modal */
.black-bg{position:fixed; padding:20px; width:100%; height:100%; background:rgba(0,0,0, 0.5);}
.white-bg{width:100%; background:#fff; border-radius:8px; padding:20px;}
</style>