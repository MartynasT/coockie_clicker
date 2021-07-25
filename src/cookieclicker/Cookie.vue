<template>
    <div class="cookie">
      <h1>Cookie vue: 🍪 {{fullData.points}} | {{upgrade}}</h1>
      <button @click="clickCookie">
        <img src="../assets/cookie.png" alt="">
      </button>
    </div>
</template>

<script>
export default {
  name: 'Cookie',
  props: ['fullData', 'upgrade'],
  data(){
    return {
      // image: '../assets/bg.jpg'

      // points: ,
      // upgrade: 1,
    }
  },
  methods: {
    clickCookie(){
      this.fullData.points += this.upgrade
      // this.$emit('points', this.points)
    }
  }
}
</script>

<style scoped>
  button{
    background: none;
    border: none;
    outline: none;
    cursor: pointer;
  }

  img{
    width: 400px;
    height: 400px;
    object-fit: contain;
  }

  .cookie{
    padding-top: 60px;
  }
  h1{
    margin-bottom: 40px;
  }

</style>