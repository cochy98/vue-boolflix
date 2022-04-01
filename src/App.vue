<template>
  <div id="app">
    <!-- Recupero dall'header la ricerca dell'utente -->
    <Header @userSearch="searchMovie" />
    <!-- Trasmetto al main la ricerca sopra ottenuta -->
    <Main :movieToSearch="movieSearched" />
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
      movieSearched: "",
    };
  },
  methods: {
    searchMovie(searchResult) {
      console.log(
        `Comunico al parent App l'utente quale film intende ricercare: ${searchResult}`
      );
      // Immagazzino in memoria il risultato della ricerca
      this.movieSearched = searchResult;
    },
  },
};
</script>

<style lang="scss">
/* Importo il mio foglio di stile */
@import "./assets/scss/style.scss";
</style>
