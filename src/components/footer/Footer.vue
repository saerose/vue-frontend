<template>
  <div class="footer">
    <Company></Company>
    <Sites></Sites>
    <Safety></Safety>
    <Customer></Customer>
    <SignUp></SignUp>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../styles'
  .footer
    +flex($direction: row, $justify: space-between)
    height: 40vh
    padding: 1vw
    margin-left: calc(50% - 50vw)
    margin-right: calc(50% - 50vw)
    background-color: $white-smoke
    border-top: 0.01em solid $magenta
</style>

<script>
  import Company from './company/Company'
  import Sites from './sites/Sites'
  import Safety from './safety/Safety'
  import Customer from './customer/Customer'
  import SignUp from './sign-up/SignUp'

  export default {
    name: 'Footer',
    components: {
      Company,
      Sites,
      Safety,
      Customer,
      SignUp
    }
  }
</script>