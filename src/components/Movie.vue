<template>
    <div class="movie">
        <img class="poster" :src="getPoster()" alt="">
        <div class="details">
            <h3>{{movie.title}}</h3>
            <ul>
                <li><span class="movie-info">Titolo Originale:</span> {{movie.original_title}}</li>
                <li v-if="movie.original_language === 'en'"><span class="movie-info">Lingua:</span> <img src="../assets/flag-united-kingdom.png" alt=""></li>
                <li v-else-if="movie.original_language === 'it'"><span class="movie-info">Lingua:</span> <img src="../assets/flag-italy.png" alt=""></li>
                <li v-else><span class="movie-info">Lingua estera</span> <img src="../assets/white-flag.png" alt=""></li>
                <li><span class="movie-info">Voto:</span> {{movie.vote_average}}</li>
            </ul>
            <p v-if="movie.overview.length > 0">{{movie.overview.slice(0, 300)}}...</p>
            <p v-else>Nessuna descrizione disponibile.</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Movie',
    props: {
        movie: Object
    },
    data() {
        return {
            posterSrc: ''
        }
    },
    methods: {
        getPoster() {
            if (this.movie.poster_path === null) {
                this.posterSrc = '../src/assets/movie_placeholder.png'

            } else {
                this.posterSrc = 'https://image.tmdb.org/t/p/original' + this.movie.poster_path
                return this.posterSrc
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    .movie {
        background-color: rgba($color: #ffffff, $alpha: .1);
        color: white;
        margin: 10px;
        width: calc(20% - 20px);
        min-height: 100%;
        position: relative;
        .poster {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        &:hover .details {
            display: block;
        }
        .details {
            padding: 30px;
            background: rgba($color: #000000, $alpha: .9);
            position: absolute;
            top: 0;
            left: 0;
            bottom: 0;
            right: 0;
            display: none;
            transition: all .2s ease;
            h3 {
                margin-bottom: 20px;
            }
            ul {
                margin-bottom: 20px;
                li {
                    list-style: none;
                    font-weight: normal;
                    margin-top: 10px;
                    font-size: .9rem;
                    width: 80%;
                    img {
                        height: 1.2rem;
                    }
                }
            }
            &::after {
                content: '';
                flex: auto;
            }
            .movie-info {
                color: #e50914;
                font-weight: bold;
            }
        }
    }
</style>