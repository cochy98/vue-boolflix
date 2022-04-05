<template>
  <div id="app">
    <!-- Recupero dall'header tramite '$emit' la lista dei film che sossisfano ricerca dell'utente -->
    <Header @movieList="searchedMovie" @TVSeriesList="searchedTVSeries" />
    <!-- Trasmetto al main la lista dei film ricevuta dall'header -->
    <Main :moviesSearched="movieList" :seriesSearched="TVSeriesList" />
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
      TVSeriesList: [],
    };
  },
  methods: {
    // Questa funzione memorizza in una variabile l'array contenente i film che soddisfano la ricerca. Ottenuta tramite una '$emit'
    searchedMovie(searchResult) {
      this.movieList = searchResult;
    },
    searchedTVSeries(searchResult) {
      this.TVSeriesList = searchResult;
    },
  },
};
</script>

<style lang="scss">
/* Import font-awesome 5 */
@import "~@fortawesome/fontawesome-free/css/all.min.css";
/* Importo il mio foglio di stile */
@import "./assets/scss/style.scss";
</style>
