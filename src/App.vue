<template>
  <div id="app">
    <!-- Recupero dall'header tramite '$emit' la lista dei film che sossisfano ricerca dell'utente -->
    <Header
      @userSearch="getUserSearch"
      @movieList="searchedMovie"
      @TVSeriesList="searchedTVSeries"
    />
    <!-- Trasmetto al main la lista dei film ricevuta dall'header -->
    <Main
      :userSearch="userSearch"
      :moviesSearched="movieList"
      :seriesSearched="TVSeriesList"
    />
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
      userSearch: "",
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
    // Questa funzione memorizza in una variabile la ricerca dell'utente. Ottenuta tramite una '$emit'
    getUserSearch(searchResult) {
      this.userSearch = searchResult;
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
