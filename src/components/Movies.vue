<template>
    <div class="container">
        <MovieCard />
    </div>
</template>

<script>
import MovieCard from './MovieCard.vue';

export default {
    name: "Movies",
    props: {
        //define variables
    },
    data() {
        return {
            //initialize variables
        };
    },
    methods: {},
    components: { MovieCard }
}
</script>

<style scoped></style>