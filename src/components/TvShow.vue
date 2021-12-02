<template>
    <div class="tvshow">
        <h3>{{tvshow.name}}</h3>
        <ul>
            <li><span class="tvshow-info">Titolo Originale:</span> {{tvshow.original_name}}</li>
            <li v-if="tvshow.original_language === 'en'"><span class="tvshow-info">Lingua:</span> <img src="../assets/flag-united-kingdom.png" alt=""></li>
            <li v-else-if="tvshow.original_language === 'it'"><span class="tvshow-info">Lingua:</span> <img src="../assets/flag-italy.png" alt=""></li>
            <li v-else><span class="tvshow-info">Lingua estera</span> <img src="../assets/white-flag.png" alt=""></li>
            <li><span class="tvshow-info">Voto:</span> {{tvshow.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'TvShow',
    props: {
        tvshow: Object
    }
}
</script>

<style lang="scss" scoped>
    .tvshow {
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
        .tvshow-info {
            color: blue;
            font-weight: bold;
        }
    }
</style>