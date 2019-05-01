<template>
  <div class="header">
    <h1 class="header__title">
      <span class="header__title-xconfessions">XConfessions</span><span class="header__title-by"> by you & Erika Lust</span>
    </h1>
    <Login></Login>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../styles'
  .header
    +flex ($direction: row, $justify: space-between, $align: center)
    font-family: 'Source Sans Pro', sans-serif
    -webkit-font-smoothing: antialiased
    -moz-osx-font-smoothing: grayscale
    padding: 1vw
    .header__title
      font-size: 1.5em
      color: $magenta
      .header__title-xconfessions
        font-weight: 700
      .header__title-by
        font-weight: 300
</style>

<script>
  import Login from '../../components/login/Login.vue'

  export default {
    name: 'Header',
    components: {
      Login
    }
  }
</script>