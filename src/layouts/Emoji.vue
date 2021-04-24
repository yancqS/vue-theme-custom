<template>
  <div class="container_emoji">
    <el-input 
      class="search-box"
      placeholder="Search your Emoji  ( Automatically remove spaces🤪  )"
      v-model="emoji"
      @input="handleInput"
    ></el-input>
    <el-card 
      v-for="(item, index) in emoji_key_arr" 
      :key="item"
      class="emoji_wrap"
      shadow="hover"
    >
      <div class="desc" @click="copyDesc(item, $event)">:{{item}}:</div>
      <div class="icon" @click="copyIcon(full_emoji[item], $event)">{{full_emoji[item]}}</div>
    </el-card>
  </div>
</template>
<script>
import {full_emoji} from '../asset/full.js';

export default {
  data() {
    return {
      emoji: '',
      full_emoji,
      emoji_key_arr: [],
      emoji_key_arr_bak: []
    }
  },
  created() {
    this.emoji_key_arr = Object.keys(full_emoji);
    this.emoji_key_arr_bak = this.emoji_key_arr.slice(0);
  },
  methods: {
    copyDesc(value, e) {
      window.getSelection().selectAllChildren(e.target)
      document.execCommand('copy');
      this.$notify({
        dangerouslyUseHTMLString: true,
        customClass: 'emoji_notify',
        message: `Hey, Emoji <code style="background: black; color: white; font-weight: bolder; border-radius: 5px; padding: 2px;">:${value}:</code> copied to the clipboard 🚀`,
        position: 'top-left',
        showClose: false,
        duration: 1500
      })
    },
    copyIcon(value, e) {
      window.getSelection().selectAllChildren(e.target)
      document.execCommand('copy');
      this.$notify({
        customClass: 'emoji_notify',
        message: `Hey, Emoji ${value } copied to the clipboard 🍻`,
        position: 'top-left',
        showClose: false,
        duration: 1500
      })
    },
    handleInput(val) {
      let reg = /\s/g;
      val = val.replace(reg, '');
      if(val) {
        this.emoji_key_arr = this.emoji_key_arr_bak.filter(item => item.includes(val))
      } else {
        this.emoji_key_arr = this.emoji_key_arr_bak.slice(0);
      }
    }
  },
}
</script>
<style lang='stylus'>
.container_emoji
  display flex
  flex-wrap wrap
  justify-content space-around
  padding 20px
  .search-box
    margin 0 20px 0 11px
  .emoji_wrap
    margin 10px 10px 0 0
    flex 0 1 23%
    &>div
      display flex
      flex-wrap nowrap
      .desc
        flex 6
        cursor pointer
        overflow hidden
        white-space nowrap
        text-overflow ellipsis
      .desc::selection
        background transparent
      .icon
        flex 1
        cursor pointer
      .icon:hover, .icon.focus
        animation-name bounce
        animation-duration 0.5s
      .icon::selection
        background transparent
  .emoji_wrap:hover, .emoji_wrap:focus
    font-weight bolder

.emoji_notify
  width 390px !important
@media only screen and (max-width: 992px) {
  .container .emoji_wrap{
    flex: 0 1 30%
  }
}
@media only screen and (max-width: 768px) {
  .container .emoji_wrap{
    flex: 0 1 48%
  }
}
@media only screen and (max-width: 576px) {
  .container .emoji_wrap{
    flex: 0 1 95%
  }
}

@media only screen and (max-width: 390px) {
  .emoji_notify {
    width: 90% !important
  }
}

@keyframes bounce {
  from,
  20%,
  53%,
  80%,
  to {
    animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
    transform: translate3d(0, 0, 0);
  }

  40%,
  43% {
    animation-timing-function: cubic-bezier(0.755, 0.05, 0.855, 0.06);
    transform: translate3d(0, -9px, 0);
  }

  70% {
    animation-timing-function: cubic-bezier(0.755, 0.05, 0.855, 0.06);
    transform: translate3d(0, -5px, 0);
  }

  90% {
    transform: translate3d(0, -2px, 0);
  }
}
</style>