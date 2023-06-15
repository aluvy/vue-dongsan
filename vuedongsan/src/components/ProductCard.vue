<template>
    <img :src="a.image" class="room-img">
    <h4 @click="모달창열렸니=1; 누른거=i;">{{ a.title }}</h4>
    <p>{{ a.content }}</p>
    <p>{{ a.price }}원</p>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    원룸들: Object,
    a: Object,
    i: Number
  }
}
</script>

<style>

</style>