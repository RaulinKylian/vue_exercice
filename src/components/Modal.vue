<template>
  <div class="bloc-modale" v-if="revele">
    <div class="modal-overlay" v-on:click="toggleModale">
      <div class="modal">
        <div v-on:click="toggleModale"></div>
          <h6>x</h6>
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
      props:['revele','toggleModale']
  }
  </script>