<template>
    <div class="movie">
        <h3>{{movie.title}}</h3>
        <ul>
            <li><span class="movie-info">Titolo Originale:</span> {{movie.original_title}}</li>
            <li v-if="movie.original_language === 'en'"><span class="movie-info">Lingua:</span> <img src="../assets/flag-united-kingdom.png" alt=""></li>
            <li v-else-if="movie.original_language === 'it'"><span class="movie-info">Lingua:</span> <img src="../assets/flag-italy.png" alt=""></li>
            <li v-else><span class="movie-info">Lingua estera</span> <img src="../assets/white-flag.png" alt=""></li>
            <li><span class="movie-info">Voto:</span> {{movie.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Movie',
    props: {
        movie: Object
    }
}
</script>

<style lang="scss" scoped>
    .movie {
        background-color: rgba($color: #ffffff, $alpha: .1);
        color: white;
        margin: 10px;
        padding: 20px;
        width: calc(20% - 20px);
        min-height: 100%;
        h3 {
            margin-bottom: 20px;
        }
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
        &::after {
            content: '';
            flex: auto;
        }
        .movie-info {
            color: #e50914;
            font-weight: bold;
        }
    }
</style>