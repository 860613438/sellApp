<template>
  <div id="app">
    <Header :seller=seller>seller</Header>
    <Nav></Nav>
    <div class="content">
      <router-view/>
    </div>
  </div>
</template>

<script>
import Header from '@/components/header/header'
import Nav from '@/components/header/nav'
export default {
  name: 'App',
  components: {
    Header,
    Nav
  },
  data () {
    return {
      seller: {
        type: String
      },
      goods: {
        type: String
      },
      ratings: {
        type: String
      }
    }
  },
  created () {
    this.$http.get('https://860613438.github.io/data.json').then(response => {
      const res = response.body
      this.seller = res.seller
      this.goods = res.goods
      this.ratings = res.ratings
    }, response => {
      // error callback
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
