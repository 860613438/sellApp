
<template>
  <div class='header'>
    <div class="header_wrap_top">
      <div class="seller_img">
        <img :src="seller.avatar">
      </div>
      <div class="seller_intro">
        <span class="seller_title">
          <i></i>
          {{seller.name}}
        </span>
        <span class="seller_intro_details">{{seller.description}}/{{seller.deliveryTime}}分钟送达</span>
        <span class="seller_offer" v-if="seller.supports && seller.supports.length > 0">
          <i :class="iconMap[seller.supports[0].type]"></i>{{seller.supports[0].description}}
        </span>
        <span class="infor_count_wrap" @click="showLabelType">{{seller && seller.supports && seller.supports.length || "0"}}个人<i class="infor_count icon-keyboard_arrow_right"></i></span>
      </div>
    </div>
    <div class="header_wrap_note">
      <div class="note_icon"></div>
      <div class="note_txt">{{seller.bulletin}}</div>
      <i class="icon_arrow icon-keyboard_arrow_right" @click="showLabelType"></i>
    </div>
    <oMask :seller="seller" v-show="showLabel"></oMask>
  </div>
</template>
<script>
import mask from '@/components/header/mask'
export default {
  components: {
    'oMask': mask
  },
  props: ['seller'],
  data () {
    return {
      showLabel: false
    }
  },
  created () {
    this.iconMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
  },
  methods: {
    showLabelType () {
      this.showLabel = !this.showLabel
    }
  }
}
</script>
<style lang="scss" rel="stylesheet/scss" scoped>
  @import "../../common/scss/mixin.scss";
  @import "../../common/scss/font.css";
  .header {
    text-align: left;
    background: rgba(0, 0, 0, .5);
    .header_wrap_top {
      display: flex;
      padding: 24px 12px 18px 24px;
      .seller_img {
        display: inline-block;
        vertical-align: top;
        width: 64px;
        height: 64px;
        margin-right: 16px;
        img {
          width: 100%;
          height: 100%;
        }
      }
      .seller_intro {
        position: relative;
        flex: 1;
        span {
          display: block;
          color: rgba(255, 255, 255, 1);
        }
        .seller_title {
          font-size: 16px;
          color: rgba(255, 255, 255,1);
          font-weight: bold;
          line-height: 18px;
          padding-bottom: 8px;
          i {
            display: inline-block;
            width: 30px;
            height: 18px;
            vertical-align: top;
            @include bg-images('brand');
            background-size: 30px 18px;
            background-repeat: no-repeat;
          }
        }
        .seller_intro_details {
          font-weight: 200;
          line-height: 12px;
          font-size: 12px;
          padding-bottom: 10px;
        }
        .seller_offer {
          font-size: 10px;
          font-weight: 200;
          line-height: 12px;
          i {
            margin-right: 2px;
          }
        }
      }
      .infor_count_wrap {
        position: absolute;
        right: 0;
        bottom: -0;
        height: 24px;
        line-height: 24px;
        border-radius: 12px;
        background: rgba($color: #000, $alpha: 0.2);
        font-size: 10px;
        padding: 0 8px;
        i {
          margin-top: 6px;
        }
      }
    }
    .header_wrap_note {
      position: relative;
      height: 28px;
      line-height: 28px;
      background: rgba(7, 17, 27, .2);
      color: #fff;
      padding: 0 27px 0 38px;
      .note_icon {
        position: absolute;
        left: 12px;
        top: 8px;
        width: 22px;
        height: 12px;
        @include bg-images('bulletin');
      }
      .note_txt {
        font-size: 10px;
        line-height: 28px;
        height: 28px;
        font-weight: 200;
        color: #fff;
        @include text-overflow();
      }
      .icon_arrow {
        position: absolute;
        top: 6px;
        right: 15px;
        width: 16px;
        height: 16px;
      }
    }
  }
</style>
