<template>
    <div class="tvshow">
        <img class="poster" :src="getPoster()" alt="">
        <div class="details">
            <h3>{{tvshow.name}}</h3>
            <ul>
                <li><span class="tvshow-info">Titolo Originale:</span> {{tvshow.original_name}}</li>
                <li v-if="tvshow.original_language === 'en'"><span class="tvshow-info">Lingua:</span> <img src="../assets/flag-united-kingdom.png" alt=""></li>
                <li v-else-if="tvshow.original_language === 'it'"><span class="tvshow-info">Lingua:</span> <img src="../assets/flag-italy.png" alt=""></li>
                <li v-else><span class="tvshow-info">Lingua estera</span> <img src="../assets/white-flag.png" alt=""></li>
                <li><span class="movie-info">Voto:</span><i class="fas fa-star" v-for="i in getScore()" :key="i"></i><i class="far fa-star" v-for="i in getEmptyStar()" :key="i"></i></li>
            </ul>
            <p v-if="tvshow.overview.length > 0">{{tvshow.overview.slice(0, 300)}}...</p>
            <p v-else>Nessuna descrizione disponibile.</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TvShow',
    props: {
        tvshow: Object
    },
    data() {
        return {
            posterSrc: '',
            score: '',
            empty: ''
        }
    },
    methods: {
        getPoster() {
            if (this.tvshow.poster_path == null) {
                this.posterSrc = '../assets/movie_placeholder.png'

            } else {
                this.posterSrc = 'https://image.tmdb.org/t/p/original' + this.tvshow.poster_path
                return this.posterSrc
            }
        },
        getScore() {
            this.score = Math.round(this.tvshow.vote_average / 2)
            return this.score
        },
        getEmptyStar() {
            this.empty = 5 - this.score
            return this.empty
        }
    }
}
</script>

<style lang="scss" scoped>
    .tvshow {
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
            h3 {
                margin-bottom: 20px;
            }
            ul {
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
            .tvshow-info {
                color: blue;
                font-weight: bold;
            }
        }
    }
</style>