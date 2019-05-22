
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
      </div>
    </div>
    <div class="header_wrap_note">
      <div class="note_icon"></div>
      <div class="note_txt">ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大ad啊大大</div>
      <i></i>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  props: ['seller'],
  data () {
    return {
    }
  },
  created () {
    this.iconMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
  }
}
</script>
<style lang="scss" rel="stylesheet/scss" scoped>
  @import "../../common/scss/mixin.scss";
  .header {
    text-align: left;
    background: rgba(0, 0, 0, .5);
    .header_wrap_top {
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
        display: inline-block;
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
            display: inline-block;
            width: 12px;
            height: 12px;
            vertical-align: top;
            background-size: 12px 12px;
            background-repeat: no-repeat;
            &.decrease {
              @include bg-images('decrease_1');
            }
            &.discount {
              @include bg-images('discount_1');
            }
            &.guarantee {
              @include bg-images('guarantee_1');
            }
            &.invoice {
              @include bg-images('invoice_1');
            }
            &.special {
              @include bg-images('special_1');
            }
          }
        }
      }
    }
    .header_wrap_note {
      position: relative;
      height: 28px;
      line-height: 28px;
      background: rgba(7, 17, 27, .2);
      color: #fff;
      padding: 0 20px;
      .note_icon {
        position: absolute;
        left: -20px;
      }
      .note_txt {
        @include text-overflow();
      }
      i {
        position: absoult;
      }
    }
  }
</style>
