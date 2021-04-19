<template>
  <div>
    <el-card
      align="center"
      class="mx-auto zoomIn mb-3 about-card"
      shadow="hover"
    >
      <div class="card-header rounded p-3">
        <div class="rounded-circle card-img-bg d-inline-block">
          <img
            :src="$withBase($themeConfig.about.image)"
            :alt="$themeConfig.about.fullName"
            width="100%"
          >
        </div>
        <h1 class="mt-2 text-light">
          {{ $themeConfig.about.fullName }}
        </h1>
      </div>
      <div class="p-3">
        <p>{{ $themeConfig.about.bio }}</p>
      </div>
      <hr class="mt-0">
      <ul
        v-if="contact"
        class="list-inline m-0"
      >
        <li
          v-for="item in contact"
          :key="item.text"
          class="list-inline-item"
        >
          <NavLink :link="item.link">
            <span :class="item.iconComponent" class="iconfont"></span>
          </NavLink>
        </li>
      </ul>
    </el-card>
  </div>
</template>

<script>
import '../asset/iconfont.css'

export default {
  computed: {
    contact () {
      return (
        (this.$themeConfig.footer && this.$themeConfig.footer.contact) ||
        []
      )
        .map(({ type, link }) => {
          return {
            iconComponent: 'icon-'+ type,
            link,
          }
        })
    },
  },
}
</script>

<style lang="stylus" scoped>
.about-card {
  max-width 35rem;
  .card-header {
    min-height: 220px;
    background-color: darken($accentColor, 10%);
  }

  .card-img-bg {
    background: $accentColor;
    background: linear-gradient(to right, $accentColor, lighten($accentColor, 30%));
  }
}
</style>
