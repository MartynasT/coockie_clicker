<template>
  <div class="shop-wrapper">
    <div class="shop-modal">
      <button class="closeShop" @click="closeShop">Close</button>
      <h2>Shop</h2>
      <h3>points {{fullData.points}}</h3>
      <h3>LVL {{upgrade}}</h3>
      <div class="buttons">
        <button :disabled="fullData.points < 10"  @click="upgradeClick(2,10)">+2 per click | 10 🍪</button>
        <button :disabled="fullData.points < 50"  @click="upgradeClick(5,50)">+5 per click | 50 🍪</button>
        <button :disabled="fullData.points < 100"  @click="upgradeClick(10,100)">+10 per click | 100 🍪</button>
        <button :disabled="fullData.points < 60"  @click="upgradeBg">New bg | 60 🍪</button>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  props: ['modalStatus' ,'fullData', 'upgrade'],
  name: 'Shop',
  data(){
    return{
      showShop: this.modalStatus
    }
  },
  methods: {
    closeShop(){
      this.showShop = !this.showShop
      this.$emit('toggleModal',this.showShop )
    },
    upgradeClick(plus, price){
      if(this.fullData.points >= price){
        this.upgrade += plus
        this.fullData.points = this.fullData.points -price
        // this.$emit('points',this.fullData.points )
      }
      this.$emit('upgrade', this.upgrade)
    },
    upgradeBg(){
      if(this.fullData.points >= 60){
        this.fullData.image = require('../assets/bg.jpg')
        this.fullData.points = this.fullData.points -60
      }
    }
  }
}
</script>

<style scoped>
  .shop-wrapper{
    position: fixed;
    width: 100%;
    height: 100%;
    inset: 0;
    background-color: rgba(0,0,0,0.5);
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .shop-modal{
    width: 50%;
    background-color: #fff;
    border-radius: 40px;
    padding: 40px;
  }

  h2{
    margin-bottom: 20px;
    margin-top: 20px;
  }
  h3{
    margin-bottom: 16px;
  }

  .buttons{
    display: flex;
    flex-wrap: wrap;
  }

  button{
    background: none;
    border: 2px solid #2c3e50;
    display: inline-block;
    color: #2c3e50;
    padding: 4px 16px;
    font-size: 20px;
    border-radius: 8px;
    margin: 5px;
    cursor: pointer;
  }

  button:hover{

  }

</style>