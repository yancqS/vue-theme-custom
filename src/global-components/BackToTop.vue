<template>
  <div v-if="top > 500" class="backToTop" @click="backtotop">🚀</div>
</template>

<script>
export default {
  data() {
    return {
      top: 0,
      ua: '',
      isChrome: '',
      isFirefox: ''
    };
  },
  mounted() {
    this.ua = navigator.userAgent.toLowerCase();
    this.isChrome =
      this.ua.includes("chrome") && this.ua.includes("safari") && !this.ua.includes("edge");
    this.isFirefox = this.ua.includes("firefox");
    window.onscroll = (e) => {
      this.top = document.documentElement.scrollTop;
    };
  },
  methods: {
    backtotop() {
      if (this.isChrome || this.isFirefox) {
        window.scrollTo({
          top: 0,
          behavior: "smooth",
        });
      } else {
        let cb = () => {
          if (document.documentElement.scrollTop === 0) {
            this.top = 0;
            return;
          } else {
            let speed = 50;
            this.top = document.documentElement.scrollTop -= speed;
            requestAnimationFrame(cb);
          }
        };
        requestAnimationFrame(cb);
      }
    },
  },
};
</script>

<style lang="stylus" scoped>
.backToTop {
  position: fixed;
  bottom: 3vh;
  right: 2vw;
  transform: rotate(-45deg);
  font-size: 2rem;
  cursor: pointer;
}
</style>