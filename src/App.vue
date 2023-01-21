
<script >
import { resolveComponentType } from '@vue/compiler-core';
import { def } from '@vue/shared';
import axios from 'axios';

  export default {
    name:'App',
    data(){
      return{
        films: null,
      }
    },
    mounted(){
      axios
      .get('https://api.themoviedb.org/3/movie/now_playing?api_key=7a4c83706af8cbec688d9366d2f9ecd2&language=fr')
      .then((reponse) => {
        this.films = reponse.data.results;
        console.log(this.films)
      });
    },
  }

</script>


<template>
<header>
  
  <section class="banner">
    <div id="logo">
      <img src="./assets/Movies_Moment.png" alt="logo">
    </div>
    <div class="title">
      <h1>Les films du moment</h1>
    </div>
  </section>
</header>
<body>
  <section class="Filter">
    <h1 class="title-filter">filtres</h1>
      <div class="filtered-buttons">
       <button class="Featured" v-on:click="films_vedette">En vedette</button>
        <button class="top-rated" v-on:click="Les-mieux-notés">Les mieux notés</button>
      </div>
  </section>
  <div :key="index" v-for="(film, index) in films">
        <img :src="'https://image.tmdb.org/t/p/w500' + film.poster_path">
        <h1>{{ film.title }}</h1>
    </div>
</body>
<footer>
    <div class="logo_footer">
      <img src="./assets/Movies_Moment.jpg" alt="logo">
    </div>
</footer>
  <main>

  </main>

</template>

