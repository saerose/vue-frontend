<template>
  <div class="films">
    <div class="films__header">
      <div class="films__header-elements">
        <div class="films__header-elements__title">Films</div>
        <div class="films__header-elements__filters">
          <div class="films__header-elements__filters-categories">Categories ↓</div>
          <Search :updateList="this.update"></Search>
        </div>
      </div>
    </div>
    <FilmsList :list="movieList"></FilmsList>
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


</style>

<script>
  import FilmsList from './films-list/FilmsList'
  import Search from './search/Search'
  export default {
    name: 'Films',
    data () {
      return {
        movieList: []
      }
    },
    components: {
      FilmsList,
      Search
    },
    methods: {
      update (list) {
        this.movieList = list
      }
    }
  }
</script>