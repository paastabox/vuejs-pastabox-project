<template>
    <div>
        <MovieSearch @searchMovieEmit="setMovieSearch" />
        {{ searchMovie }}
        <MovieList :movies="movies" :searchMovie="searchMovie" @showMovieDetailEmit="movieDetail" />
        <MovieDetail v-if="selectedMovie" :movie="selectedMovie" @close="closeDetail" />
    </div>
</template>

<script>
import axios from 'axios';
import config from '@/config.json';
import MovieDetail from '@/components/MovieDetail.vue';
import MovieList from '@/components/MovieList.vue';
import MoviePagination from '@/components/MoviePagination.vue';
import MovieSearch from '@/components/MovieSearch.vue';

export default {
    name: 'HomeView',
    components: {
        MovieDetail,
        MovieList,
        MoviePagination,
        MovieSearch
    },

    data() {
        return {
            selectedMovie: null,
            movies: [],
            searchMovie: ''
        }
    },

    beforeMount() {
        console.log('beforeMount');
        // axios api call
        axios.request({
            headers: {
                Authorization: 'Bearer ' + config.api_key
            },
            method: "GET",
            url: config.url.movie_list
        }).then(response => {
            this.movies = response.data.results;
            console.log("Get movie okay");
            console.log(this.movies);
        }).catch(error => {
            console.error(error);
        });
    },

    methods: {
        movieDetail(movie) {
            this.selectedMovie = movie;
        },

        closeDetail() {
            this.selectedMovie = null;
        },

        setMovieSearch(search) {
            this.searchMovie = search;
        }
    },
}

</script> 