<template>
  <div>
    <img :src="product.image" class="room-img"/>
    <h4 @click="$emit('openModal')">{{product.title}}</h4>
    <p>{{product.price}}원</p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  methods: {
    fn_detail(index) {
      console.log("index",index);
      this.modalIndex = index;
      modalStatus = true;
    }
  },
  props: {
    modalStatus: Boolean,
    modalIndex: Number,
    product: Object,
  }
}
</script>

<style>
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>