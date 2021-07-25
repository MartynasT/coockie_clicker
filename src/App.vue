<template>
  <div id="app" :style="{ backgroundImage: 'url(' + fullData.image + ')' }" >
    <Cookie :fullData="fullData" :upgrade="upgrade" @points="points = $event"  />
    <Shop
        v-if="showShop"
        :modalStatus="showShop"
        @toggleModal="showShop = $event"
        @upgrade="upgrade = $event"
        @points="points = $event"
        :fullData="fullData"
        :upgrade="upgrade"
    />
    <button class="shopbutton" @click="toggleShopModal">Shop</button>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import SayHello from '@/components/SayHello'
import Card from '@/components/Card'
import Card2 from '@/components/Card2'
import Card3 from '@/components/Card3'
import Random from '@/components/Random'
import Inputs from '@/components/Inputs'
import Quiz from '@/components/Quiz'
import Cookie from '@/cookieclicker/Cookie'
import Shop from '@/cookieclicker/Shop'

export default {
  name: 'App',
  components: {
    HelloWorld,
    SayHello,
    Card,
    Card2,
    Card3,
    Random,
    Inputs,
    Quiz,
    Cookie,
    Shop

  },
  data(){
    return{
      // points: 0,
      upgrade: 1,
      showShop: false,
      fullData:{
        points: 0,
        image: ''
      }
    }
  },
  methods:{
    toggleShopModal(showShop){
      this.showShop = !this.showShop
    }
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*display: flex;*/
  justify-content: space-evenly;
  padding: 0;
  margin: 0;
  min-height: 100vh;
  background-repeat: no-repeat;
  background-size: cover;
}

.shopbutton{
  background: none;
  border: 2px solid #2c3e50;
  display: inline-block;
  color: #2c3e50;
  padding: 8px 40px;
  font-size: 20px;
  border-radius: 8px;
}
</style>
