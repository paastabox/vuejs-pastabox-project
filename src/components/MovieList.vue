<template>
    <div>
        <!-- list of movies -->
        <v-card variant="outlined" v-for="movie in movies">
            <v-card-title>
                {{ movie.title }}
            </v-card-title>
            <v-img :src="config.url.image + movie.poster_path" />
        </v-card>
    </div>
</template>

<script>
import config from '@/config.json';

export default {
    name: 'MoviesList',
    data() {
        return {
            movies: []
        }
    },
    beforeMount() {
        console.log('beforeMount');
        const options = {
            method: 'GET',
            headers: {
                accept: 'application/json',
                Authorization: 'Bearer ' + config.api_key
            }
        };

        fetch(config.url.movie_list, options)
            .then(response => response.json())
            .then(data => {
                this.movies = data.results;
            })
            .catch(error => console.error(error));     
    }
}

</script>