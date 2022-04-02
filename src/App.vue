<template>
  <div id="app">
    <!-- Recupero dall'header tramite '$emit' la lista dei film che sossisfano ricerca dell'utente -->
    <Header @movieList="searchedMovie" />
    <!-- Trasmetto al main la lista dei film ricevuta dall'header -->
    <Main :moviesSearched="movieList" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      movieList: [], // Array che contiene la lista dei film passati da 'Header.vue'
    };
  },
  methods: {
    // Questa funzione memorizza in una variabile l'array contenente i film che soddisfano la ricerca. Ottenuta tramite una '$emit'
    searchedMovie(searchResult) {
      this.movieList = searchResult;
    },
  },
};
</script>

<style lang="scss">
/* Importo il mio foglio di stile */
@import "./assets/scss/style.scss";
</style>
