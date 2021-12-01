<template>
    <div class="movie">
        <h3>{{movie.title}}</h3>
        <h4>{{movie.original_title}}</h4>
        <h4>{{movie.original_language}}</h4>
        <h4>{{movie.vote_average}}</h4>
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
            margin-bottom: 10px;
        }
        h4 {
            font-weight: normal;
        }
        &::after {
            content: '';
            flex: auto;
        }
    }
</style>