<template>
    <main>
        <Movie v-for="movie, i in searchResult" :key="i" :movie="movie" />
    </main>
</template>

<script>
import Movie from '@/components/Movie.vue'
export default {
    name: 'MainCont',
    components: {
        Movie,
    },
    props: {
        searchRes: Array
    },
    computed: {
        searchResult() {
                return this.searchRes
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