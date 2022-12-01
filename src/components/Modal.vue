<template>
  <div class="black-bg" v-if="modalStatus == true">
    <div class="white-bg">
      <img :src="product.image" class="room-img"/>
      <h4>{{product.title}}</h4>
      <p>{{product.content}}</p>
      <input v-model="month">
      <input v-model="month" type="range" min="1" max="24"/>
      <p> {{ month }} 개월 선택함 : {{product.price * month}}원</p>
      <Discount/>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>

import Discount from '@/components/Discount.vue';

export default {
  name: 'Modal',
  data() {
    return {
        month: 1,
    }
  },
  components: {
    Discount: Discount,
  },
  watch: {
    month(nVal, oVal) {
        console.log("month",nVal, oVal);
        if (isNaN(nVal) == true) {
            alert("문자입력금지!!!");
            this.month = oVal;
        }
    }
  },
  props: {
    modalStatus: Boolean,
    product: 
    Object,
  }
}
</script>

<style>
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>