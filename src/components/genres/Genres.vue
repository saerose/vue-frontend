<template>
  <div class="genres-list">
    <div class="genres-list__element" v-for="genre of genres">
      <span class="genres-list__element-name">{{genre.name}}</span>
    </div>
  </div>
</template>

<style lang="sass" scoped>
  @import '../../styles'
  .genres-list
    +flex($direction: row, $justify: space-between)
    margin-top: 6vh
    padding: 1vw
    .genres-list__element
      width: 20vh
      height: 8vh
      padding: 2vh
      background-color: $magenta
      border-radius: 0.2em
      .genres-list__element-name
        font-family: 'Source Sans Pro', sans-serif
        color: $white
        font-size: 1.2em
        font-weight: 700
</style>

<script>
  export default {
    name: 'Genres',
    components: {
    },
    data() {
      return {
        genres: [],
        baseUrl: `https://api.themoviedb.org/3/genre/movie/list?api_key=${process.env.VUE_APP_API_KEY_V3}&language=en-US
`
      }
    },
    methods: {
      fetchData() {
        return fetch(this.baseUrl)
          .then((response) => response.json())
          .then((body) => {
            this.genres = body.genres.slice(0, 6);
            console.log(this.genres)
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