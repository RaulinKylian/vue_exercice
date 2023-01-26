
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
        data: null,
        revele: false,
        clicked: null,
        tmp: null
      }
    },
    methods: {
      toggleModal: function(e){
        this.revele = !this.revele
        this.clicked = e
      },
        filter: function(){
          let tmp;
          tmp = this.films.filter((e) => e.vote_average > 7)
          this.films = tmp;
        },
        all: function(){
          this.films = this.data;
        }
      },
    mounted(){
      axios
      .get('https://api.themoviedb.org/3/movie/now_playing?api_key=7a4c83706af8cbec688d9366d2f9ecd2&language=fr')
      .then((reponse) => {
        this.films = reponse.data.results;
        this.data = reponse.data.results;
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
    <h1 class="title_filter">filtres :</h1>
      <div class="filtered_buttons">
        <button class="top_rated" v-on:click="filter">Les mieux notés</button>
        <button class="all_movies" v-on:click="all">Tous les films</button>
      </div>
  </section>
  <section class="container_Movies">
    <div class="grid_movies">
        <div :key="index" v-for="(film, index) in films">
          <div class="grid_container"  @click="showModal = true">
            <img v-on:click="toggleModal(film)" class="movies_images" :src="'https://image.tmdb.org/t/p/w500' + film.poster_path">
            <div class="movie_info">
              <h1 class="titles">{{ film.title }}</h1>
            </div>
          </div>
        </div>
    </div>
  </section>
  <Modal v-bind:revele="revele" v-bind:clicked="clicked" v-bind:toggleModale="toggleModal"/>
  
</main>
<footer>
  <section class="container_footer">
    <div class="paragraph">
      <p>2023  -  Exercice VueJS  -  Movies Moment</p>
    </div>
  </section>
</footer>

</template>

