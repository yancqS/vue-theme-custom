<template>
  <div class="busuanzi">
    <span id="busuanzi_container_site_pv">
      本站总访问量
      <span id="busuanzi_value_site_pv" />次
      <span class="post-meta-divider">|</span>
    </span>
    <span id="busuanzi_container_site_uv">
      本站访客数
      <span id="busuanzi_value_site_uv" />人
    </span>
  </div>
</template>

<script>
let script

export default {
  // 监听,当路由发生变化的时候执行
  watch: {
    $route (to, from) {
      if (to.path !== from.path) {
        script.fetch()
      }
    },
  },
  mounted () {
    script = require('busuanzi.pure.js')
  },
}
</script>
<style scoped>
.busuanzi {
  font-size: 14px;
}
</style>
