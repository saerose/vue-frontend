<template>
  <div>
    <Header></Header>
    <Banner></Banner>
  </div>
</template>


<style>
#app {
  font-family: 'Source Sans Pro', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<script>
  import Header from './containers/header/Header.vue'
  import Banner from './components/banner/Banner.vue'

  export default {
    name: 'app',
    components: {
      Header,
      Banner
    }
  }
</script>
