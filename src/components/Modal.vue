<template>
  <div class="bloc-modale" v-if="revele">
    <div class="modal-overlay" v-on:click="toggleModale">
      <div class="modal">
        <div class="container_modal" v-on:click="toggleModale"></div>
          <img class="image_modal" :src="'https://image.tmdb.org/t/p/w500' + clicked.poster_path">
          <div class="info_modal">
            <h3 class="title_modal">{{ clicked.title }}</h3>
            <p class="release_date_modal">Date de sortie : {{ clicked.release_date }}</p>
            <p class="overview_modal">{{ clicked.overview }}</p>
            <div class="container_vote">
              <p class="vote_average">Note : {{ clicked.vote_average }}</p>
            </div>
            </div>
        <div class="close">
        <button class="close-modal-button" v-on:click="close">x</button>
      </div>
      </div>
    </div>
  </div>
  </template>
  
  <script>
    export default {
      name: 'Modal',
      props:['revele','toggleModale', 'clicked']
  }
  </script>