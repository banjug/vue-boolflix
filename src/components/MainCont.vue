<template>
    <main>
        <Movie/>
    </main>
</template>

<script>
import Movie from '@/components/Movie.vue'
import axios from "axios"
export default {
    name: 'MainCont',
    components: {
        Movie,
    },
    props: {
        search: String
    },
    data() {
        return {
            apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=f6d56afba3697f4f7eaf4ee3841df221&language=en-US&query=' + this.search +'&page=1&include_adult=true',
            movieList: [],
        }
    },
    methods: {
        getMovie() {
            axios
            .get(this.apiUrl)
            .then((result) => {
                this.movieList = result.data.results
            })
        }
    }
}
</script>

<style lang="scss" scoped>
    main {
        background-color: #141414;
    }
</style>