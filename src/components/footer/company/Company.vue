<template>
  <div class="company">
    <div class="company__elements">
      <div class="company__elements-about">
        <span>Erika Lust Films</span>
        <a>About Us</a>
        <a>Affiliates</a>
        <a>How we make our films</a>
      </div>

      <div class="company__elements-address">
        Passeig Picasso 32, Pral <br/>
        08003 Barcelona – Spain <br/>
        Telf +34 931 59 69 69
      </div>
    </div>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../../styles'
  .company
    +flex($direction: column)
    font-family: 'Source Sans Pro', sans-serif
    font-size: 0.9em
    color: $nobel
    .company__elements
      .company__elements-about
        +flex($direction: column)
        span
          font-weight: 700
        a
          text-decoration: underline
          font-weight: 300
      .company__elements-address
        margin-top: 6vh
        font-weight: 300


</style>

<script>
  export default {
    name: 'Company',
    components: {
    }
  }
</script>