<template>
    <div class="films-list">
      <div class="films-list__no" v-if="noRes"><span class="films-list__no-element">BIG BADA BOOM ☄️</span></div>
      <div class="films-list__element" :style="film.backdrop_path" v-for="film of films">{{film.title}}</div>
    </div>
</template>

<style lang="sass" scoped>
  @import '../../styles'
  .films-list
    +flex($direction: row, $justify: space-between, $wrap: wrap)
    .films-list__no
      width: 100%
      margin: 4vh 30%
      .films-list__no-element
        color: $magenta
        font-size: 6em
        text-align: center
    .films-list__element
      cursor: pointer
      font-family: 'Source Sans Pro', sans-serif
      color: $white
      font-size: 1em
      font-weight: 400
      margin: 1vw 0
      background-color: lavender
      width: 29vw
      height: 18vh
      padding: 1vw
      background-position: center
      background-size: cover
</style>

<script>
  export default {
    name: 'FilmsList',
    components: {
    },
    props: {
      list: Array
    },
    data() {
      return {
        noRes: false,
        films: [],
        baseUrl: `https://api.themoviedb.org/3/discover/movie?api_key=${process.env.VUE_APP_API_KEY_V3}&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=2`,

      }
    },
    methods: {
      fetchData() {
        return fetch(this.baseUrl)
          .then((response) => response.json())
          .then((body) => this.films = this.mapResults(body.results))
          .catch(error => {
            this.error({
              status: error.status,
              message: 'Something went wrong, please try again later. 😭'
            })
          })
      },
      mapResults (res) {
        return res.slice(0, 18)
          .map(el => ({
            ...el,
            backdrop_path: {
              'background-image': `linear-gradient(to bottom right,rgba(0,0,0,1),rgba(0,0,0,0)), url(http://image.tmdb.org/t/p/original${el.backdrop_path})`
            }
          }));
      }
    },
    watch: {
      list: {
        inmediate: true,
        handler (newVal) {
          if (!newVal) {
            this.noRes = false
            this.fetchData();
          }
          else if (!newVal.length) {
            this.films = []
            this.noRes = true
          }
          else {
            this.noRes = false
            this.films = this.mapResults(newVal)
          }
        }
      }
    },
    mounted() {
      this.fetchData()
    }
  }
</script>