<template>
  <div class="sites">
    <div class="sites__elements">
      <span>Our Sites</span>
      <a>erikalust.com</a>
      <a>store.erikalust.com</a>
      <a>eroticfilms.com</a>
      <a>lustcinema.com</a>
      <a>thepornconversation.org</a>
      <a>guidetogoodporn.com</a>
    </div>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../../styles'
  .sites
    font-family: 'Source Sans Pro', sans-serif
    font-size: 0.9em
    color: $nobel
    .sites__elements
      +flex($direction: column)
      span
        font-weight: 700
      a
        text-decoration: underline
        font-weight: 300
</style>

<script>
  export default {
    name: 'Sites',
    components: {
    }
  }
</script>