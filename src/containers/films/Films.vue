<template>
  <div class="films">
    <div class="films__header">
      <div class="films__header-elements">
        <div class="films__header-elements__title">Films</div>
        <div class="films__header-elements__filters">
          <div>categories</div>
          <div>search</div>
        </div>
      </div>
    </div>
    <FilmsList></FilmsList>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../styles'
  .films
    padding: 1vw
    .films__header
      background-color: wheat
</style>

<script>
  import FilmsList from 'FilmsList.vue'
  export default {
    name: 'Films',
    components: {
      FilmsList
    },
    data() {
      return {
        films: [],
        baseUrl: `https://api.themoviedb.org/3/discover/movie?api_key=${process.env.VUE_APP_API_KEY_V3}&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=2`,

      }
    },
    methods: {
      fetchData() {
        return fetch(this.baseUrl)
          .then((response) => response.json())
          .then((body) => {
            this.films = body.results
              .slice(0, 18)
              .map(el => ({ ...el, backdrop_path: {
                  'background-image': `linear-gradient(to bottom right,rgba(0,0,0,1),rgba(0,0,0,0)), url(http://image.tmdb.org/t/p/original${el.backdrop_path})` } }));;
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