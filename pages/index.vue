<template>
 <div class="home">
   <!-- Hero -->
   <Hero/>

 </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      movies: [],
    }
  },
  async fetch() {
    await this.getMovies()
  },
  methods: {
    async getMovies() {
      const data = axios.get('https://api.themoviedb.org/3/movie/now_playing?api_key=ba7f48d120906a59bb4c8fccc134ff75&language=en-US&page=1')
      const response = await data;
      response.data.results.forEach(movie => {
        this.movies.push(movie);
      })
      console.log(this.movies)
    }
  }
}
</script>
