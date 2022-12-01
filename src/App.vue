<template>
  <!-- modal -->
  <Modal @closeModal="modalStatus = false" :modalStatus="modalStatus" :product="products[modalIndex]"/>

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{menu}}</a>
  </div>

  <Discount/>

  <Card @openModal="modalStatus = true; modalIndex = i; " v-for="(v, i) in products" :key="i" :product="v"/>
</template>

<script>

import data from '@/assets/oneroom.js';
import Discount from '@/components/Discount.vue';
import Modal from '@/components/Modal.vue';
import Card from '@/components/Card.vue';

export default {
  name: 'App',
  data() {
    return {
      menus: ['Home','Shop','About'],
      modalStatus: false,
      modalIndex: -1,
      products: data,
    }
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
  }
}
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background-color: darkgoldenrod;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

</style>
