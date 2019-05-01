<template>
  <div class="safety">
    <div class="safety__elements">
      <span>100% Safe</span>
      <a>Legal conditions</a>
      <a>Privacy policy</a>
      <a>Requirements Compliance Statement</a>
      <a>Cookies policy</a>
      <a>Billing support</a>
    </div>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../../styles'
  .safety
    font-family: 'Source Sans Pro', sans-serif
    font-size: 0.9em
    color: $nobel
    .safety__elements
      +flex($direction: column)
      span
        font-weight: 700
      a
        font-weight: 300
</style>

<script>
  export default {
    name: 'Safety',
    components: {
    }
  }
</script>