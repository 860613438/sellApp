
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
        <span class="seller_offer" v-if="seller.supports.length > 0">
          <i></i>{{seller.supports[0].description}}
        </span>
      </div>
    </div>
    <div class="header_wrap_note">

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
            @include bg-images('decrease_1');
            background-size: 12px 12px;
            background-repeat: no-repeat;
          }
        }
      }
    }
  }
</style>
