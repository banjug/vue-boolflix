<template>
    <header>
        <h1>BOOLFLIX</h1>
        <div class="search">
            <input type="text" placeholder="Cerca un film o una serie" v-model="userSearch" @keyup.enter="getMovies()">
            <button @click="getMovies()">CERCA</button>
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
            this.apiUrl = 'https://api.themoviedb.org/3/search/movie?api_key=f6d56afba3697f4f7eaf4ee3841df221&language=it-IT&query='+ this.userSearch +'&page=1&include_adult=true'
            axios
            .get(this.apiUrl)
            .then((result) => {
                this.movieList = result.data.results
                this.$emit('userSearch', this.movieList)
                return this.movieList
            })
        }
    },
}
</script>

<style lang="scss" scoped>
    header {
        height: 100px;
        background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(20,20,20,1) 100%); 
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
            width: 25%;
            * {
                font-size: 1rem;
                line-height: 2rem;
                padding: 5px 20px;
                border-radius: 30px;
                border: none;
            }
            input {
                margin-right: 10px;
                width: 100%;
            }
            button {
                font-weight: bold;
                border: 2px solid #e50914;
                background-color: transparent;
                color: #e50914;
                transition: all .1s ease;
                cursor: pointer;
                &:active {
                    background-color: #e50914;
                    color: white;
                }
            }
        }
    }
</style>