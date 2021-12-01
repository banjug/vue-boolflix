<template>
  <div id="app">
    <Header/>
    <MainCont/>
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
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
