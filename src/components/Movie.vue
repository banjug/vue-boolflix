<template>
    <div class="movie">
        <h3>{{movie.title}}</h3>
        <h4><span class="movie-info">Titolo Originale:</span> {{movie.original_title}}</h4>
        <h4><span class="movie-info">Lingua:</span> {{movie.original_language}}</h4>
        <h4><span class="movie-info">Voto:</span> {{movie.vote_average}}</h4>
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
        h3 {
            margin-bottom: 20px;
        }
        h4 {
            font-weight: normal;
            margin-top: 10px;
            font-size: .9rem;
            width: 80%;
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