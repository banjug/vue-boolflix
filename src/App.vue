<template>
  <div id="app">
    <Header @movieSearch="movieResult" @tvSearch="tvResult"/>
    <MainCont :movieRes="movieList" :tvRes="tvList"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import MainCont from './components/MainCont.vue'

export default {
  name: 'App',
  components: {
    Header,
    MainCont
  },
  data() {
    return {
      movieList: [],
      tvList: []
    }
  },
  methods: {
    movieResult(movieArray) {
      this.movieList = movieArray;
    },
    tvResult(tvArray) {
      this.tvList = tvArray;

    }
  }
}
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    background-color: #141414;
  }
</style>
