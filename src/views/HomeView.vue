<template>
    <div>
        <MovieList />
    </div>
</template>

<script>
import MovieDetail from '@/components/MovieDetail.vue';
import MovieList from '@/components/MovieList.vue';
import MoviePagination from '@/components/MoviePagination.vue';
import movieSearch from '@/components/movieSearch.vue';

export default {
    name: 'HomeView',
    components: {
        MovieDetail,
        MovieList,
        MoviePagination,
        movieSearch
    }
}

</script>