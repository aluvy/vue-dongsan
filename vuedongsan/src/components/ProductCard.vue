<template>
  <div>
    <img :src="원룸.image" class="room-img">
    <h4 @click="모달창열렸니=1; 누른거=i;">{{ 원룸.title }}</h4>
    <p>{{ 원룸.content }}</p>
    <p>{{ 원룸.price }}원</p>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    // 원룸들: Object,
    // a: Object,
    // i: Number,
    원룸: Object,
  }
}
</script>

<style>

</style>