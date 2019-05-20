<template>
  <div id="app">
    <Header></Header>
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

      }
    }
  },
  created () {
    console.log(this.$http)
    this.$http.get('./data.json').then(response => {
      console.log('0')
      console.log(response)
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
  margin-top: 60px;
}
</style>
