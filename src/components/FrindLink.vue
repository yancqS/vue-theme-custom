<template>
  <el-card
    shadow="hover"
    :body-style="{ padding: '1rem' }"
    style="margin-top: 1rem"
  >
    <ul class="list-unstyled">
      <h4 class="website">推荐网站</h4>
      <li
        v-for="item in $themeConfig.friendlink"
        :key="item.name"
        class="d-inline-block mx-2 my-2"
      >
        <el-button @click="jump(item.link)">{{item.name}}</el-button>
      </li>
    </ul>
  </el-card>
</template>

<script>
export default {
  methods: {
    jump(url) {
      window.open(url, '_blank');
    }
  }
}
</script>

<style lang="stylus">
.website
  background-image -webkit-linear-gradient(90deg, red, #fd8403, #ff0)
  -webkit-background-clip text
  -webkit-text-fill-color transparent
</style>
