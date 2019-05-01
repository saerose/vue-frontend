<template>
  <div class="customer">
    <div class="customer__elements">
      <div class="customer__elements-about">
        <span>Customer Support</span>
        <a>FAQS</a>
        <a>Contact us</a>
        <a class="customer__elements-about__gift"><span>🎁</span><div>Send a Gift Card</div></a>
      </div>
    </div>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../../styles'
  .customer
    +flex($direction: column)
    font-family: 'Source Sans Pro', sans-serif
    font-size: 0.9em
    color: $nobel
    .customer__elements
      .customer__elements-about
        +flex($direction: column)
        span
          font-weight: 700
        a
          font-weight: 300
        .customer__elements-about__gift
          +flex($direction: row, $justify: center, $align: center)
          width: 7vw
          height: 6vh
          padding: 0.6vw
          border: 0.01em solid $nobel
          span
            font-size: 1.5em


</style>

<script>
  export default {
    name: 'Customer',
    components: {
    }
  }
</script>