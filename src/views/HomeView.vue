<template>
  <div class="home">
    <form @submit.prevent="SearchMovies()" class="search-box">
      <input type="text" placeholder="Search" v-model="search">
      <input type="submit" value="Submit">
    </form>
      <div class="movies" v-for="movie in movies" :key="movie.imdbID">
        <router-link :to="'/movie/' + movie.imdbID">
          <div class="movie-info">{{movie.Title}} ({{movie.Year}})</div> 
        </router-link>
      </div>
 </div>
</template>

<script>
import { ref } from 'vue';
import env from '@/env.js'


export default {
  setup () {
    const search = ref("");
    const movies = ref([])

    const SearchMovies = () => {
      if (search.value != "") {
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
         .then(response => response.json())
         .then(data => {
           movies.value = data.Search;
           search.value = "";
         });
      }

    }
    return {
      search,
      movies,
      SearchMovies
    }
  }
}
</script>

<style lang="scss">
.home {
    .feature-card {
      position: relative;

    }
    .detail {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.6);
      padding: 16px;
      z-index: 1;
    }

    h3{
      color: white;
      margin-bottom: 20px;
    }
    p {
      color: white;
    }
    .Link {
      font-style: italic;
    }
    .search-box {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 16px;

      input {
        display: block;
        appearance: none;
        border: none;
        outline: none;
        background: none;

        &[type="text"] {
          width: 100%;
          color: black;
          background-color: rgb(255, 255, 255);
          font-size: 20px;
          padding: 10px 16px;
          border-radius: 8px;
          margin-bottom: 15px;
          transition: 0.4s;

          &::placeholder {
            color: rgb(184, 184, 184);
          }

          &:hover {
            box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.6);
          }
        }
          &[type="submit"] {
            width: 100%;
            max-width: 300px;
            background-color: rgb(255, 255, 255);
            padding: 16px;
            border-radius: 8px;
            color: rgb(184, 184, 184);
            font-size: 20px;
            text-transform: uppercase;
            transition: 0.4s;
            
            &:hover {
            box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.6);
            }

            &:active {
              background-color: rgb(243, 243, 243);
            }
          } 
      }


    }

    .movies .movie-info {
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 10px;
      align-items: center;
      color: black;
    }
}
</style>
