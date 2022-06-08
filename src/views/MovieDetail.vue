<template>
  <div class="details">
    <div><h1>{{movie.Title}} ({{movie.Year}})</h1></div>
    <div><img :src="movie.Poster" alt="Movie Poster"/></div>
    <div>{{movie.Plot}}</div>
  </div>
</template>

<script>
import {ref, onBeforeMount} from 'vue';
import {useRoute } from 'vue-router';
import env from '@/env.js';

export default {
  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
         .then(response => response.json())
         .then(data => {
           movie.value = data;
         });
    });

    return {
      movie
    }
  }
}
</script>

<style>
.details {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 10px;
  align-items: center;
}

.details div {
  padding: 10px;
}

.details h1 {
  color: black;
}

</style>