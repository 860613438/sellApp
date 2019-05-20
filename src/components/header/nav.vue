<template>
  <div class="tab">
    <ul>
      <li v-for="(nav,index) in navList" :key="nav.name" @click="toggle(index)">
        <router-link :to="nav.link">{{nav.name}}</router-link>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  components: {},
  data () {
    return {
      checkindex: 0, // 初始化第一个栏块高亮
      navList: [
        {
          name: '商品',
          link: 'goods'
        },
        {
          name: '评价',
          link: 'ratings'
        },
        {
          name: '商家',
          link: 'seller'
        }
      ],
      active: ''
    }
  },
  methods: {
    toggle (index) {
      this.checkindex = index
    }
  }
}
</script>
<style lang="scss">
.tab {
  height: 40px;
  width: 100%;
  ul {
    height: 40px;
    overflow: hidden;
    line-height: 40px;
    display: flex;
    border-bottom: 1px solid rgba(7, 17, 27, 0.1);
    li {
      flex-grow: 1;
      font-size: 14px;
      color: rgb(147, 153, 159);
    }
  }
  li .active, .router-link-active {
    color: rgb(240, 20, 20);
  }
}
</style>
