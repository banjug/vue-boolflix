<template>
    <main>
        <Movie/>
    </main>
</template>

<script>
import Movie from '@/components/Movie.vue'
export default {
    name: 'MainCont',
    components: {
        Movie,
    }
}
</script>

<style lang="scss" scoped>
    main {
        background-color: #141414;
    }
</style>