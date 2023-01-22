
<script >
import { resolveComponentType } from '@vue/compiler-core';
import { def } from '@vue/shared';
import axios from 'axios';
import Modal from './components/Modal.vue'


  export default {
    name:'App',
    components: {
      'Modal': Modal

    },
    data(){
      return{
        films: null,
        revele: false
      }
    },
    methods: {
      toggleModal: function(){
        this.revele = !this.revele
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
    <div class="logo">
      <img class="logo_img" src="./assets/Movies_Moment.png" alt="logo">
    </div>
    <div class="title_container">
      <h1 class="title">Les films du moment :</h1>
    </div>
  </section>
</header>
<main>
  <section class="Filter">
    <h1 class="title_filter">filtres</h1>
      <div class="filtered_buttons">
        <button class="top_rated" v-on:click="Les-mieux-notés">Les mieux notés</button>
      </div>
  </section>
  <section class="container_Movies">
    <div class="grid_movies">
        <div :key="index" v-for="(film, index) in films">
          <div class="grid_container"  @click="showModal = true">
            <img v-on:click="toggleModal" class="movies_images" :src="'https://image.tmdb.org/t/p/w500' + film.poster_path">
            <h1>{{ film.title }}</h1>
          </div>
        </div>
    </div>
  </section>
  <Modal v-bind:revele="revele" v-bind:toggleModale="toggleModal"/>
  
</main>
<footer>
  <section class="container_footer">
    <div class="paragraph">
      <p>2023  -  Exercice VueJS  -  Movies Moment</p>
    </div>
  </section>
</footer>

</template>

