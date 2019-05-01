<template>
  <div class="sign-up">
    <div class="sign-up__element">
      <div class="sign-up__element-text">
        <b>Sign Up!</b>
        <span class="sign-up__element-text__join">Join our mailing list and watch a film for free!</span>
      </div>
      <div class="sign-up__element-input">
        <input class="sign-up__element-input__input" placeholder="Enter your email...">
        <button>Sign Up!</button>
      </div>
      <div class="sign-up__element-checkbox">
        <input type="checkbox" id="checkbox" v-model="checked">
        <label for="checkbox">I have read and agree to the terms of use and privacy</label>
      </div>
    </div>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../../styles'
  .sign-up
    font-family: 'Source Sans Pro', sans-serif
    .sign-up__element
      +flex($direction: column)
      color: $magenta
      .sign-up__element-text
        +flex($direction: column)
        .sign-up__element-text__join
          font-size: 0.9em
          font-weight: 300
      .sign-up__element-input
        +flex($direction: row, $justify: space-between)
        margin-top: 2vh
        .sign-up__element-input__input
          width: 20vw
          height: 6vh
          border: 0.01em solid $magenta
          padding: 1vw
        button
          width: 6vw
          background-color: transparent
          border: 0.01em solid $magenta
          color: $magenta
      .sign-up__element-checkbox
        margin-top: 2vh
        font-size: 0.8em
</style>

<script>
  export default {
    name: 'SignUp',
    components: {
    }
  }
</script>