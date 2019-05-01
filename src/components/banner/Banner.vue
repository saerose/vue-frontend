<template>
  <div class="banner">
    <div class="banner__list" v-for="film in films" :style="film.backdrop_path">
      <div class="banner__list-title">{{film.original_title}}</div>
      <div class="banner__list-info">Movie info</div>
      <div class="banner__list-buttons">
        <button>Play Film</button>
        <button>Trailer</button>
        <button>Download</button>
      </div>
    </div>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../styles'
  .banner
    +flex ()
    overflow-x: auto
    width: 100vw
    height: 50vh
    margin: 0 calc(50% - 50vw)
    .banner__list
      flex: 0 0 auto
      width: 100%
      padding: 1vw
      transform: translateX(100%)
      background-position: center
      background-size: cover
      animation: iterateBanner 50s steps(10, end) infinite
      .banner__list-title
        font-weight: 700
        font-size: 3em
      .banner__list-info
        font-size: 1em
      .banner__list-buttons

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
        poster: '',
        moviePosters: '',
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
              .map(el => ({ ...el, backdrop_path: { 'background-image': `url(http://image.tmdb.org/t/p/original${el.backdrop_path})` } }));
            console.log(this.films)
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

<!--<script>
      fetchData () {
        return fetch(`https://reqres.in/api/users?page=${this.page}`)
          .then((response) => response.json())
          .then((body) => {
            this.maxPages = body.total_pages
            this.users = body.data
          })
          .catch(err => {
            this.err({
              status: err.status,
              message: 'Something went wrong whilst fetching users'
            })
          })
      },
      movePage ({target}) {
        this.page += Number(target.value)
        this.fetchData()
      }
    },
    mounted () {
      this.fetchData()
    },
    props: {
      err: Function
    }
  }
</script>-->