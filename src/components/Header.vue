<template>
  <header>
    <!-- L'utente inserisce un film da ricercare, all'invio viene richiamato il metodo 'getApiSearchedFilms' che popola la lista dei film in base all'input inserito dall'utente -->
    <nav class="navbar navbar-light">
      <div class="container">
        <a class="navbar-brand">
          <img
            src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Netflix_2015_logo.svg/1280px-Netflix_2015_logo.svg.png"
            alt="Netflix logo"
          />
        </a>
        <div class="d-flex">
          <input
            type="text"
            class="form-control me-2"
            placeholder="Search..."
            v-model.trim="inputSearch"
            @keyup.enter="
              getApiSearchedFilms(myApiKey, inputSearch, currentPage)
            "
          />
        </div>
      </div>
    </nav>
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
          console.log("Recupero la lista dei film corrispondenti");
          // Invio l'array ad 'app.vue' sul canale "movieList"
          this.$emit("movieList", this.movieList);
          // Invio il nome della ricerca ad 'app.vue' sul canale "userSearch"
          this.$emit("userSearch", search);
        })
        .catch((error) => {
          // Errore nella richiesta
          console.log(error);
          console.log("errore");
        });
      this.getApiSearchedTVSeries(apiKey, search, page);
      this.inputSearch = "";
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
          console.log("Recupero la lista delle serie TV corrispondenti");
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
nav.navbar {
  padding: 1rem;

  .navbar-brand > img {
    width: 150px;
  }
}
</style>
