<template>
  <div class="films">
    <div class="films__header">
      <div class="films__header-elements">
        <div class="films__header-elements__title">Films</div>
        <div class="films__header-elements__filters">
          <div class="films__header-elements__filters-categories">Categories ↓</div>
          <div class="films__header-elements__filters-search">🔎</div>
        </div>
      </div>
    </div>
    <FilmsList></FilmsList>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../styles'
  .films
    font-family: 'Source Sans Pro', sans-serif
    padding: 1vw
    .films__header
      .films__header-elements
        +flex($direction: row, $justify: space-between)
        .films__header-elements__title
          color: $magenta
          font-size: 1.5em
          font-weight: 400
        .films__header-elements__filters
          +flex($direction: row, $justify: space-around)
          .films__header-elements__filters-categories
            +flex($justify: center, $align: center)
            width: 25vh
            height: 6vh
            margin-right: 2vw
            border: 0.1em solid $magenta
            color: $magenta
          .films__header-elements__filters-search
            +flex($justify: center, $align: center)
            width: 6vh
            height: 6vh
            border: 0.1em solid $magenta


</style>

<script>
  import FilmsList from '../../components/films-list/FilmsList'
  export default {
    name: 'Films',
    components: {
      FilmsList
    },
  }
</script>