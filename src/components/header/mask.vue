<template>
  <div class='mask_wrap'>
    <div class="mask">
      <h1>{{seller && seller.name}}</h1>
      <!-- <div class="star"><star :score="seller.score" :size="48"></star></div> -->
      <div class="title_wrap">
        <div class="line"></div>
        <div class="title">优惠信息</div>
        <div class="line"></div>
      </div>
      <ul class="offer_list" v-if="seller && seller.supports && seller.supports.length > 0">
        <li v-for="support in seller.supports" :key="support.type">
          <i :class="iconMap[support.type]"></i>
          {{support.description}}
        </li>
      </ul>
      <div class="title_wrap">
        <div class="line"></div>
        <div class="title">商家公告</div>
        <div class="line"></div>
      </div>
      <p class="sellerNote">{{seller.bulletin}}</p>
      <p class="sellerNote">{{seller.bulletin}}</p>
      <p class="sellerNote">{{seller.bulletin}}</p>
      <p class="sellerNote">{{seller.bulletin}}</p>
      <p class="sellerNote">{{seller.bulletin}}</p>
      <p class="sellerNote">{{seller.bulletin}}</p>
      <p class="sellerNote">{{seller.bulletin}}</p>
      <p class="sellerNote">{{seller.bulletin}}</p>
    </div>
    <div class="icon_close"><i class="icon_bottom_close icon-close1" @click="getParentLabelType"></i></div>
    <!-- <star :score="seller.score" :size="48"></star> -->
  </div>
</template>
<script>
export default {
  props: ['seller'],
  // components: { star },
  data () {
    return {
    }
  },
  created () {
    this.iconMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
  },
  methods: {
    getParentLabelType () {
      this.$parent.showLabelType()
    }
  }
}
</script>
<style lang="scss" rel="stylesheet/scss" scoped>
@import '../../common/scss/mixin';
@import '../../common/scss/font.css';
.mask_wrap {
  position: fixed;
  width: 100%;
  height: calc(100% - 64px);
  z-index: 1;
  left: 0;
  top: 0;
  background: rgba(7, 17, 27, .8);
  color: #fff;
  padding-bottom: 64px;
  .mask {
    width: 100%;
    height: 100%;
    overflow-y: scroll;
    -webkit-overflow-scrolling: touch;
    h1 {
      font-size: 16px;
      line-height: 16px;
      text-align: center;
      font-weight: 700;
      color: #fff;
      margin-top: 64px;
    }
    .star {
      text-align: center;
    }
    .title_wrap {
      width: 100%;
      display: inline-block;
      text-align: center;
      margin: 28px 0 24px;
      .line, .title {
        display: inline-block;
      }
      .line {
        width: 112px;
        border-top: 1px solid rgba(255, 255, 255, .2);
      }
      .title {
        padding: 0 20px;
        font-size: 14px;
        font-weight: 700;
        line-height: 14px;
      }
    }
    .offer_list {
      padding: 0 36px;
      text-align: left;
      font-size: 12px;
      li {
        height: 16px;
        line-height: 16px;
        margin: 6px 0;
        i {
          display: inline-block;
          width: 16px;
          height: 16px;
          overflow: hidden;
          margin-right: 6px;
          vertical-align: top;
        }
      }
    }
    .sellerNote {
      padding: 0 12px;
      font-size: 12px;
      font-weight: 200;
      line-height: 24px;
    }
  }
  .icon_close {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 64px;
    font-size: 32px;
    color: rgba(255, 255, 255, 0.5);
    background: rgba(7, 17, 27, 0.8);
    text-align: center;
    .icon_bottom_close {
      display: inline-block;
      width: 32px;
      height: 32px;
    }
  }
}
</style>
