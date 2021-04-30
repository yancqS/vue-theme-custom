<template>
  <div v-if="top > 500" class="backToTop" @click="backtotop">🚀</div>
</template>

<script>
export default {
  data() {
    return {
      top: 0
    }
  },
  mounted() {
    window.onscroll = (e) => {
      this.top = document.documentElement.scrollTop || document.body.scrollTop;
    }
  },
  methods: {
    backtotop() {
      window.scrollTo({
        top: 0,
        behavior: "smooth"
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
.backToTop
  position fixed
  bottom 3vh
  right 2vw
  transform rotate(-45deg)
  font-size 2rem
  cursor pointer
</style>