<template>
    <header>
        <h1>BOOLFLIX</h1>
        <div class="search">
            <input type="text" placeholder="Cerca un film o una serie" v-model="userSearch" @keyup.enter="getMovies(),$emit('userSearch', movieList)">
            <button @click="getMovies(),$emit('userSearch', movieList)">Cerca</button>
        </div>
    </header>
</template>

<script>
import axios from "axios"
export default {
    name: 'Header',
    data() {
        return {
            userSearch: '',
            apiUrl: '',
            movieList: [],
        }
    },
    methods: {
        getMovies() {
            this.apiUrl = 'https://api.themoviedb.org/3/search/movie?api_key=f6d56afba3697f4f7eaf4ee3841df221&language=en-US&query='+ this.userSearch +'&page=1&include_adult=true'
            axios
            .get(this.apiUrl)
            .then((result) => {
                this.movieList = result.data.results
                return this.movieList
            })
        }
    },
}
</script>

<style lang="scss" scoped>
    header {
        background-color: #141414;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 20px 30px;
        h1 {
            color: #e50914;
            font-size: 3rem;
        }
        .search {
            display: flex;
            input {
                margin-right: 10px;
                padding: 5px 10px;
                border: none;
                border-radius: 20px;
            }
            button {
                padding: 5px 10px;
                border: none;
                border-radius: 20px;
                background-color: #e50914;
                color: white;
            }
        }
    }
</style>