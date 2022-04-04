<template>
  <header>
    <!-- L'utente inserisce un film da ricercare, all'invio viene richiamato il metodo 'getApiSearchedFilms' che popola la lista dei film in base all'input inserito dall'utente -->
    <input
      type="text"
      placeholder="Inserisci il titolo del film da ricercare"
      v-model="inputSearch"
      @keyup.enter="getApiSearchedFilms(myApiKey, inputSearch, currentPage)"
    />
  </header>
</template>

<script>
/* Importo Axios per gestire la chiamata all'Api */
import axios from "axios";
export default {
  name: "IndexHeader",
  data() {
    return {
      myApiKey: "f617480c0a93aca25c95f2b70e2824ca",
      inputSearch: "",
      movieList: [],
      TVSeriesList: [],
      currentPage: 1,
    };
  },
  methods: {
    /* Effettuo una richiesta GET all'Api ed inserisco i valori nell'array 'movieList'. Lo trasmetto ad 'App.vue' tramite un '$emit' */
    getApiSearchedFilms(apiKey, search, page) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&query=${search}&page=${page}`
        )
        .then((result) => {
          // Richiesta andata a buon fine
          // Inserisco il risultato della ricerca nell'array e stampo un messaggio a video
          this.movieList = result.data.results;
          console.log("Recupero la lista dall'API");
          // Invio l'array ad 'app.vue' sul canale "movieList"
          this.$emit("movieList", this.movieList);
        })
        .catch((error) => {
          // Errore nella richiesta
          console.log(error);
          console.log("errore");
        });
      this.getApiSearchedTVSeries(apiKey, search, page);
    },
    getApiSearchedTVSeries(apiKey, search, page) {
      axios
        .get(
          `https://api.themoviedb.org/3/search/tv?api_key=${apiKey}&query=${search}&page=${page}`
        )
        .then((result) => {
          // Richiesta andata a buon fine
          // Inserisco il risultato della ricerca nell'array e stampo un messaggio a video
          this.TVSeriesList = result.data.results;
          console.log("Recupero la lista dall'API");
          // Invio l'array ad 'app.vue' sul canale "movieList"
          this.$emit("TVSeriesList", this.TVSeriesList);
        })
        .catch((error) => {
          // Errore nella richiesta
          console.log(error);
          console.log("errore");
        });
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  height: 100px;
  background-color: rgb(196, 108, 108);
}
</style>
