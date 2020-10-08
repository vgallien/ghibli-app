<template>
    <div class="container mx-auto flex flex-wrap">
        <div v-bind:key='index' v-for='(movie, index) in movies' class="w-1/5 px-4 my-2">
            <img :src="movie.poster" alt="" title="" class="block" />
            <h2 class="text-center">{{ movie.title }}</h2>
        </div>
    </div>
</template>

<script>

import axios from 'axios'

export default {
    name: 'MovieList',
    data() {
        return {
            movies: []
        }
    },
    mounted() {
        axios
        .get('https://ghibliapi.herokuapp.com/films')
        .then(reponse => {
            for (const movie of reponse.data) {
                axios
                .get('https://api.themoviedb.org/3/search/movie?api_key=ce76939574157ed69c1f81c691bfbe63&query=' + movie.title)
                .then(reponse2 => {
                    const poster = "https://image.tmdb.org/t/p/w500/" + reponse2.data.results[0].poster_path
                    this.movies.push({
                        title: movie.title,
                        poster
                    });
                })
            }
            
        })
    }
    
}
</script>

<style scoped>

</style>
