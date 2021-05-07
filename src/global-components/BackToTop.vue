<template>
  <div v-if="top > 500" class="backToTop" @click="backtotop">🚀</div>
</template>

<script>
const ua = navigator.userAgent.toLowerCase();

const isChrome = ua.includes("chrome") && ua.includes("safari") && !ua.includes("edge");
const isFirefox = ua.includes("firefox");

export default {
  data() {
    return {
      top: 0,
    };
  },
  mounted() {
    window.onscroll = (e) => {
      this.top = document.documentElement.scrollTop;
    };
  },
  methods: {
    backtotop() {
      if (isChrome || isFirefox ) {
        window.scrollTo({
          top: 0,
          behavior: "smooth",
        });
      } else {
        let cb = () => {
          if(document.documentElement.scrollTop===0) {
            this.top = 0;
            return;
          } else {
            let speed = 50;
            this.top = document.documentElement.scrollTop -= speed;
            requestAnimationFrame(cb);
          }
        }
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