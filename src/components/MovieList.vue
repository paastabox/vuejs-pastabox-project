<template>
    <div v-for="movie in movieFiltered" style="padding: 10px">
        <v-card class="text-center" variant="outlined" style="padding: 10px">
            <v-img :src="photo_path + movie.poster_path" :alt="movie.title" width="300px" class="mx-auto"
                aspect-ratio="1" />
            <v-card-title class=text-center>
                {{ movie.title }}
            </v-card-title>
            <v-card-text class=text-center>
                {{ movie.overview }}
            </v-card-text>
            <v-btn variant="outlined" @click="sendMovie(movie)">
                Plus d'infos
            </v-btn>
        </v-card>
    </div>
</template>

<script>
import config from '@/config.json';
import MovieDetail from '@/components/MovieDetail.vue';

export default {
    name: 'MoviesList',

    props: {
        movies: {
            type: Array,
            required: true
        },
        searchMovie: {
            type: String,
            required: true
        }
    },

    data() {
        return {
            photo_path: config.url.photo_path
        };
    },

    computed: {
        movieFiltered() {
            console.log(this.searchMovie);
            if (this.searchMovie) {
                return this.movies.filter(movie => {
                    return movie.title.toLowerCase().includes(this.searchMovie.toLowerCase());
                });
            }
            return this.movies;
        }
    },
    
    components: { MovieDetail },

    methods: {
        sendMovie(movie) {
            this.$emit('showMovieDetailEmit', movie);
        }
    },
}

</script>