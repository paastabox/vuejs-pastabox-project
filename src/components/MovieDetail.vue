<template>
    <div>
        <!-- detail vue (v-dialog or something like this) -->
        <!-- Je n'ai pas réussi à utiliser le v-overlay -->
    </div>
</template>
<script>
import axios from 'axios';

export default {
    name: 'MovieDetail',

    props: {
        movie: Object,
        // overlay: Boolean
    },

    data() {
        return {
            show: true,
        }
    },

    created() {
        // axios.get(this.$route.query.page + `/${this.movieid}`)
        //     .then(response => {
        //         this.movieid = response.data;
        //     })
        //     .catch(error => {
        //         console.error(error);
        //     });

    },

    methods: {
        closeDetail() {
            this.$emit('close');
            console.log('closeDetail');
        },
    }
}

</script>