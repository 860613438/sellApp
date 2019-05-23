<template>
  <div class='star' :class="starType">
    <span v-for="(itemClass,index) in itemClasses" :key="index" :class="itemClass" class="star-item"></span>
  </div>
</template>
<script>
const LENGTH = 5
const CLS_ON = 'on'
const CLS_HALF = 'half'
const CLS_OFF = 'off'
export default {
  props: {
    size: {
      type: Number
    },
    score: {
      type: Number
    }
  },
  computed: {
    starType () {
      return 'star-' + this.size
    },
    itemClasses () {
      let result = []
      let score = Math.floor(this.score * 2) / 2
      let hasDecimal = score % 1 !== 0
      let integer = Math.floor(score)
      for (let i = 0; i < integer; i++) {
        result.push(CLS_ON)
      }
      if (hasDecimal) {
        result.push(CLS_HALF)
      }
      while (result.length < LENGTH) {
        result.push(CLS_OFF)
      }
      return result
    }
  },
  data () {
    return {

    }
  }
}
</script>
<style lang="scss" rel="stylesheet/scss" scoped>
@import "../../common/scss/mixin.scss";
.star {
  font-size: 0;
  .star-item {
    background-size: 100% 100%;
    display: inline-block;
    background-repeat: no-repeat;
  }
  &.star-48 {
    .star-item {
      width: 20px;
      height: 20px;
      margin-right: 22px;
      &.on {
        @include bg-images('star48_on');
      }
      &.half {
        @include bg-images('star48_half');
      }
      &.off {
        @include bg-images('star48_off');
      }
      &:last-child {
        margin-right: 0;
      }
    }
  }
  &.star-36 {
    .star-item {
      width: 15px;
      height: 15px;
      margin-right: 10px;
      &.on {
        @include bg-images('star36_on');
      }
      &.half {
        @include bg-images('star36_half');
      }
      &.off {
        @include bg-images('star36_off');
      }
      &:last-child {
        margin-right: 0;
      }
    }
  }
  &.star-24 {
    .star-item {
      width: 10px;
      height: 10px;
      margin-right: 3px;
      &.on {
        @include bg-images('star24_on');
      }
      &.half {
        @include bg-images('star24_half');
      }
      &.off {
        @include bg-images('star24_off');
      }
      &:last-child {
        margin-right: 0;
      }
    }
  }
}
</style>
