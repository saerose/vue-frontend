<template>
  <div class="search">
    <div class="search__no" v-if="!showInput" v-on:click="toggleSearchInput">🔎</div>
    <div v-if="showInput">
      <input class="search__yes" v-model="userQuery" v-on:change="search" type="text" placeholder="🔍 Search...">
      <span class="search__yes-close" v-on:click="toggleSearchInput">✕</span>
    </div>
  </div>
</template>
<style lang="sass" scoped>
  @import '../../../styles'
  .search
    .search__no
      +flex($justify: center, $align: center)
      cursor: pointer
      width: 6vh
      height: 6vh
      border: 0.1em solid $magenta
    .search__yes
      border: none
      width: 25vh
      height: 6vh
      &:focus
        outline: none
    .search__yes-close
      cursor: pointer
      color: $magenta
</style>

<script>
  export default {
    name: 'Search',
    components: {
    },
    data() {
      return {
        showInput: false,
        userQuery: '',
        searchResponse: [],
        genBaseUrl: () => `https://api.themoviedb.org/3/search/movie?api_key=${process.env.VUE_APP_API_KEY_V3}&language=en-US&query=${encodeURIComponent(this.userQuery)}&page=1&include_adult=false`
      }
    },
    props: {
      updateList: Function
    },
    methods: {
      toggleSearchInput() {
        this.updateList(undefined)
        this.showInput = !this.showInput
      },
      search() {
        setTimeout(() => {
          return fetch(this.genBaseUrl())
            .then((response) => response.json())
            .then((body) => {
              this.searchResponse = body.results;
              this.updateList(this.searchResponse)
            })
            .catch(error => {
              this.error({
                status: error.status,
                message: 'Something went wrong, please try again later. 😭'
              })
            })
        }, 1000)
      }
    },
    mounted() {
    }
  }
</script>