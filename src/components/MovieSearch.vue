<template>
    <div>
        <v-text-field
            v-model="search"
            append-icon="search"
            label="Search"
            single-line
            hide-details
        ></v-text-field>
    </div>
</template>
<script>
export default {
    name: 'MovieSearch',
    data() {
        return {
            search: ''
        }
    },
    watch: {
        search() {
            this.$emit('searchMovieEmit', this.search);
        }
    }
}
</script>