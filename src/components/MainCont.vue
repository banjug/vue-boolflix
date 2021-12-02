<template>
    <main>
        <Movie v-for="movie, i in movieResult" :key="i" :movie="movie" />
        <TvShow v-for="tvshow, j in tvShowResult" :key="j" :tvshow="tvshow" />
    </main>
</template>

<script>
import Movie from '@/components/Movie.vue'
import TvShow from '@/components/TvShow.vue'
export default {
    name: 'MainCont',
    components: {
        Movie,
        TvShow
    },
    props: {
        movieRes: Array,
        tvRes: Array
    },
    computed: {
        movieResult() {
                return this.movieRes
        },
        tvShowResult() {
            return this.tvRes
        }
    }
}
</script>

<style lang="scss" scoped>
    main {
        width: 90%;
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        min-height: calc(100vh - 100px);
    }
</style>