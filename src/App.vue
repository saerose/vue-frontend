<template>
  <div>
    <Header></Header>
    <Banner></Banner>
    <Genres></Genres>
    <Films></Films>
    <Footer></Footer>
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
  import Header from './components/header/Header'
  import Footer from './components/footer/Footer'
  import Banner from './components/banner/Banner'
  import Genres from './components/genres/Genres'
  import Films from './components/films/Films'

  export default {
    name: 'app',
    components: {
      Header,
      Footer,
      Banner,
      Genres,
      Films
    }
  }
</script>
