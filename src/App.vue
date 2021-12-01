<template>
  <div id="app">
    <Header @userSearch="searchResult"/>
    <MainCont :searchResult="search"/>
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
      search: ''
    }
  },
  methods: {
    searchResult(movieArray) {
      this.search = movieArray;
      console.log(this.search);
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
  }
</style>
