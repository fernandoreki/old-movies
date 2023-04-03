<template>
    <div class="row row justify-content-center bg-secondary p-5">
        <div class="card m-2" v-for="(movie, idx) in 10" :key="idx" style="width: 20rem;">
        <ul class="p-2">
            <ol class="col" >
                <br>
                <img v-if="images[idx] !== null" :src="images[idx]" alt="image" class="card-img-top img-fluid">
                <img v-else="images[idx]" src="../assets/image-not-found.png" alt="image" class="card-img-top img-fluid">
                <div class="card-body text-dark">
                    <h3 class="card-title">{{ movies?.results[idx].titleText.text }}</h3> <br>
                    <p>
                        Title type: {{ movies?.results[idx].titleType.text }} <br>
                        Year: {{ movies?.results[idx].releaseYear.year }}
                    </p>
                </div>

            </ol>
        </ul>
    </div>
    </div>
    
</template>

<script>
import axios from "axios";
export default {
    name: 'MovieCard',
    props: {
        //define variables
    },
    async mounted() {
        await this.getMovies()
        this.isMounted = true;
    },
    data() {
        return {
            //initialize variables
            movies: null,
            images: ['https://m.media-amazon.com/images/M/MV5BZDI4MmJiMmMtMzQ3Mi00N2Y0LTlkYmUtYmQ0ZTQ1NzVlZmVjXkEyXkFqcGdeQXVyMDUyOTUyNQ@@._V1_FMjpg_UX1000_.jpg'
                , 'https://i.ytimg.com/vi/J1Tyj1wkXSg/maxresdefault.jpg'
                , 'https://pics.filmaffinity.com/Galileo-131316351-mmed.jpg'
                , 'https://m.media-amazon.com/images/M/MV5BMWY2ODg0YWEtZDVmYy00OTEwLTkxN2YtYzY5ZmRmNjVlZWYyXkEyXkFqcGdeQXVyMDUyOTUyNQ@@._V1_.jpg'
                , 'https://m.media-amazon.com/images/M/MV5BZDU3YzM0NTEtMzczMS00M2FkLWJiMzQtMGViZTZmODZkNjAyXkEyXkFqcGdeQXVyMDUyOTUyNQ@@._V1_.jpg'
                , 'https://www.lavanguardia.com/peliculas-series/images/movie/poster/1911/9/w1280/fWEQy9Y3LZlN7oDa96fpS8MTHGc.jpg'
                , 'https://m.media-amazon.com/images/M/MV5BOGRmZWJhMjAtZjVhZS00ZjA3LTkwODUtMjZhYTJlNGNhMDEzXkEyXkFqcGdeQXVyMzg1ODEwNQ@@._V1_.jpg'
                , 'https://kbhbilleder.dk/danmarkpaafilm/32/thumbnail/500.jpg'
                , 'https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Prudent-Louis_Leray_-_Poster_for_the_premi%C3%A8re_of_Georges_Bizet%27s_Carmen.jpg/320px-Prudent-Louis_Leray_-_Poster_for_the_premi%C3%A8re_of_Georges_Bizet%27s_Carmen.jpg'
                , 'https://pics.filmaffinity.com/fiskerliv_i_norden_aka_fiskernes_liv_i_norden_s-400822123-mmed.jpg']
        }
    },
    methods: {
        getMovies() {

            const options = {
                method: 'GET',
                url: 'https://moviesdatabase.p.rapidapi.com/titles',
                headers: {
                    'X-RapidAPI-Key': '054519b369mshc592475765dd6abp195e71jsn26afe0d6c042',
                    'X-RapidAPI-Host': 'moviesdatabase.p.rapidapi.com'
                }
            };
            axios.request(options)
                .then(response => {
                    this.movies = response.data;
                })
                .catch(error => console.log(error));
        }
    }
}
</script>

<style scoped>
img {
    width: 200px;
}


</style>