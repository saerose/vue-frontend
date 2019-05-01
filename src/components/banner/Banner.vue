<template>
  <div class="banner__list">
    <div class="banner__list-element" v-for="film in films" :style="film.backdrop_path">
      <div class="banner__list-element__content">
        <div class="banner__list-element__content-title">{{film.original_title}}</div>
        <div class="banner__list-element__content-info">
          <span class="banner__list-element__content-info__date"><b>Release date: </b>{{film.release_date}}</span>
          <span class="banner__list-element__content-info__overview">{{film.overview}}</span>
        </div>
        <div class="banner__list-element__content-buttons">
          <button class="banner__list-element__content-buttons__element">Play Film</button>
          <button class="banner__list-element__content-buttons__element">Trailer</button>
          <button class="banner__list-element__content-buttons__element">Download</button>
        </div>
      </div>
    </div>
    <div class="banner__gradient"></div>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../styles'
  .banner__list
    +flex ()
    overflow-x: hidden
    width: 100vw
    height: 70vh
    margin-left: calc(50% - 50vw)
    margin-right: calc(50% - 50vw)
    .banner__list-element
      z-index: -1
      flex: 0 0 auto
      width: 100%
      padding: 1vw
      transform: translateX(100%)
      background-position: center
      background-size: cover
      animation: iterateBanner 50s steps(10, end) infinite
      color: $white
      .banner__list-element__content
        position: absolute
        bottom: 0
        margin-bottom: 4vh
        font-family: 'Source Sans Pro', sans-serif
        .banner__list-element__content-title
          font-weight: 700
          font-size: 3em
        .banner__list-element__content-info
          +flex($direction: column)
          width: 25vw
          margin-bottom: 1vh
          .banner__list-element__content-info__date
            font-size: 0.8em
          .banner__list-element__content-info__overview
            font-size: 0.9em
        .banner__list-element__content-buttons
          cursor: pointer
          .banner__list-element__content-buttons__element
            width: 14vw
            height: 7vh
            background-color: transparent
            border: 0.1em solid $white
            color: $white
            text-transform: none
            font-weight: 300
            margin: 0 3vw 0 0
            font-size: 1.5em

  @keyframes iterateBanner
    from
      transform: translateX(0%)
    to
      transform: translateX(-1000%)
</style>

<script>
  export default {
    name: 'Banner',
    components: {
    },
    data() {
      return {
        films: [],
        baseUrl: `https://api.themoviedb.org/3/discover/movie?api_key=${process.env.VUE_APP_API_KEY_V3}&language=en-US&sort_by=popularity.desc&include_adult=true&include_video=false&page=1`
      }
    },
    methods: {
      fetchData() {
        return fetch(this.baseUrl)
          .then((response) => response.json())
          .then((body) => {
            this.films = body.results
              .slice(0, 10)
              .map(el => ({ ...el, backdrop_path: {
                'background-image': `linear-gradient(to bottom right,rgba(0,0,0,1),rgba(0,0,0,0)), url(http://image.tmdb.org/t/p/original${el.backdrop_path})` } }));
          })
          .catch(error => {
            this.error({
              status: error.status,
              message: 'Something went wrong, please try again later. 😭'
            })
          })
      },
    },
    mounted() {
      this.fetchData()
    }
  }
</script>